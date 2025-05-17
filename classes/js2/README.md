<!-- {"layout": "title"} -->
# **JavaScript** parte 2
## Estrutura de competição, vetores, mais sobre funções e métodos úteis de strings


---
<!-- {"layout": "centered"} -->
# Hoje veremos...

1. [Estruturas de Repetição](#repeticao)
1. [Vetores](#condicionais-vetores-e-estruturas-de-repeticao)
1. [Mais sobre funções e Métodos úteis](#mais-sobre-funcoes-e-metodos-uteis)


---
<!-- {"layout": "section-header", "hash": "repeticao"} -->
# Estruturas de repetição
## _Arrays_, for, while e variações
- Intuição, acumulador e valores máximos
- For
    - Tradicional
    - For of
    - forEach
- While/Do while
<!-- {ul^1:.content} -->

---
# **for** <small>(forma tradicional)</small>

- <!-- {ul:no-margin} -->
  ::: did-you-know .push-right width:240px;
  Em JavaScript há pelo menos 3 formas diferentes de fazer um `for`. Esta é a **tradicional** mas as outras mais fáceis até.
  :::
  Forma tradicional com `for (inicio; condicao; incremento)`:
  ```js
  for (let i = 0; i < 10; i++) {
    console.log(i);               // 0, 1, 2 ... 9
  }
  ```
<style>
    .countBig{
      font-size: 3em;
      text-align: center;
      position: relative;
      left: 38%;
      border-radius: 50%;
      background-color: purple;
      width: 120px;
      color: white;

    }
</style>  


---
<!-- {"layout": "2-column-content"} -->
# while/do..while

- Condição **primeiro** <!-- {ul:.no-bullets} -->
  ```js
  let i = 1;
  while (i !== 10) {
    console.log(i);
    i++;
  }
  ```
1. Condição **depois** <!-- {ol:.no-bullets} -->
   ```js
   let i = 0;
   do {
     i++;
     console.log(i);
   } while (i !== 10);
   ```

---
---
<!-- {"layout": "section-header", "hash": "vetores"} -->
# Vetores
## Listas de coisas

- Declaração de vetores
- Iteração em vetores
- atributos e métodos comuns de vetores
<!-- {ul:.content} -->

---
# Vetores

- Vetores (ou _arrays_) armazenam uma sequência de valores: <!-- {ul:.bulleted-0.compact-code} -->
  ```js
  let notas = [10, 4, 7, 8, 8];
  let cores = ['azul', 'verde'];
  let animais = []; // <- vetor vazio
  ```
- ```js
  console.log(notas.length);  // impr. 5
  console.log(cores.length);  // impr. 2
  ```
  Assim como _string_, um vetor tem um **comprimento** (propriedade `length` <!-- {style="float:none"} -->): <!-- {li:.push-code-right style="margin-top: 0.25em;"} -->
- Em JavaScript, vetores são heterogêneos
  - Os itens dos vetores **não** precisam ter o mesmo tipo
    ```js
    let listaDeCoisas = ['Aew', 35, true, [], 'outra string'];
    ```
---
<!-- {"elementStyles": { "h2 + pre": "overflow: hidden; width: 100%;"}} -->
## **Usando** vetores

```js
let listaDeCoisas = ['Aew', 35, true, [], 'outra string'];
```

- Indexação: usa-se os símbolos `[` e `]` para acessar um item do _array_ <!-- {ul:.bulleted} -->
  ```js
  console.log(listaDeCoisas[1]);      // imprime 35
  listaDeCoisas[0] = '';              // altera primeiro elemento
  console.log(listaDeCoisas[0]);      // imprime string vazia
  ```
- _Arrays_ possuem métodos, [vários](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) (veremos outros mais adiante):
  ```js
  let frutas = [];                    // cria um array vazio
  frutas.push('kiwi');                // coloca 'kiwi' no array
  console.log(frutas);                // imprime ['kiwi']
  ```
---
# Intuição - como você calcularia o somatório desses números?

5<!-- {p:.countBig} -->

---
# Intuição - como você calcularia o somatório desses números?

3<!-- {p:.countBig} -->

---
# Intuição - como você calcularia o somatório desses números?

1<!-- {p:.countBig} -->

---
# Intuição - como você calcularia o somatório desses números?

7<!-- {p:.countBig} -->

---
# Intuição - como você calcularia o somatório desses números?

2<!-- {p:.countBig} -->

---
# Intuição - **Somatório*

- Você provavelmente:
  1. **Guardou** o valor do somatorio 
  1. A medida que aparecia um novo número, **acumulava** ele nesse valor "guardado"

- Essa é a mesma forma que fará em programação. Possuindo: 
  1. Uma lista de números
  1. Uma variável que acumula o somatório até então
  1. Uma variável para armazenar o valor da posição atual


---
<!-- {"layout": "2-column-content", "classes": "compact-code-more"} -->
# Intuição - Somatórios
<style>
    .smallCode{
      code{
        font-size: 0.5em;
        
      }
      list-style-type: none;
      line-height: 1em;

    }
</style>  




1. **Sem Vetores e sem for**: ❌❌ <!-- {ol:.bulleted} -->
   ```js
    function fazSoma(){
      let acumulador = 0;
      acumulador += 5;
      acumulador += 3;
      acumulador += 1;
      acumulador += 7;
      return acumulador;
    }
    fazSoma();
   ```
- **Com vetores, sem for**: ❌ <!-- {ul:.bulleted} -->
  ```js
  function fazSoma(listaDeNumeros){
    let acumulador = 0;
    acumulador += listaDeNumeros[0];
    acumulador += listaDeNumeros[1];
    acumulador += listaDeNumeros[2];
    acumulador += listaDeNumeros[3];
    return acumulador;
  }
  let minhaListaLinda = [5, 3, 1, 7];
  fazSoma(minhaListaLinda);
  ```



---
<!-- {"layout": "2-column-content", "classes": "compact-code-more"} -->
# Somatório com for tradicional

1. **Sem Vetores e sem for** ❌❌ <!-- {li:.smallCode} --><!-- {ol:.bulleted} -->
   ```js
    function fazSoma(listaDeNumeros){
      let acumulador = 0;
      acumulador += listaDeNumeros[0];
      acumulador += listaDeNumeros[1];
      acumulador += listaDeNumeros[2];
      acumulador += listaDeNumeros[3];
      return acumulador;
    }
    let minhaListaLinda = [5, 3, 1, 7];
    fazSoma(minhaListaLinda);   
    ```
- **Com for tradicional**: :thumbsup: <!-- {li:.smallCode} --><!-- {ul:.bulleted} -->
  ```js
  function fazSoma(listaDeNumeros){
    let acumulador = 0;
    for(let i = 0 ; i < listaDeNumeros.length ; i++){
      acumulador += listaDeNumeros[i];
    }
    return acumulador;
  }
  let minhaListaLinda = [5, 3, 1, 7];
  fazSoma(minhaListaLinda);
  ```
---
<!-- {"layout": "2-column-content", "classes": "compact-code-more"} -->
# Somatório com for mais elegante

1. **Com for tradicional** :thumbsup: <!-- {li:.smallCode} --><!-- {ol:.bulleted} -->
   ```js
    function fazSoma(listaDeNumeros){
      let acumulador = 0;
      for(let i = 0 ; i < listaDeNumeros.length ; i++){
        acumulador += listaDeNumeros[i];
      }
      return acumulador;
    }
    let minhaListaLinda = [5, 3, 1, 7];
    fazSoma(minhaListaLinda);
    ```
- **Com for of - para cada** :thumbsup::thumbsup: <!-- {li:.smallCode} --><!-- {ul:.bulleted} -->
  ```js
  function fazSoma(listaDeNumeros){
    let acumulador = 0;
    for(let valorAtual of listaDeNumeros){
      acumulador += valorAtual;
    }
    return acumulador;
  }
  let minhaListaLinda = [5, 3, 1, 7];
  fazSoma(minhaListaLinda);
  ```


---
<!-- {"layout": "2-column-content", "hash": "for-formas-mais-legais"} -->
# **for** <small>(formas **mais legais**)</small>

1. **For of**: `for (let item of array)` :thumbsup:: <!-- {ol:.no-bullets} -->
   ```js
   let cores = ['azul', 'rosa'];
   for (let cor of cores) {
     console.log(cor);
     // azul, rosa
   }
   ```
- **For each**: `array.forEach` :thumbsup:: <!-- {ul:.no-bullets} -->
  ```js
  let cores = ['azul', 'rosa'];
  cores.forEach(function(cor) {
    console.log(cor);
    // azul, rosa
  });
  ```



---
<!-- {"hash": "metodos-comuns-de-vetores-1"} -->
## **Métodos** comuns de **vetores** (1/3)

- Assim como as strings, os vetores também possuem vários métodos úteis
  
  `vetor.length`
    ~ não é método, mas retorna tamanho do vetor
    ~ `[5].length === 1`

  `vetor[i]`
    ~ não é método, mas retorna i-ésimo elemento
    ~ `[3, 10][0] === 3`
    ~ ```js
      let letras = ['x'];
      letras[0] = 'y';
      ```

---
<!-- {"hash": "metodos-comuns-de-vetores-2"} -->
## **Métodos** comuns de **vetores** (2/3)

`vetor.push(elem)`
  ~ método que insere `elem` ao final do vetor
  ~ `['a'].push('b') === ['a', 'b']`

`vetor.pop()`
  ~ método que remove último elemento
  ~ `['a', 'b'].pop() === ['a']`

`vetor.indexOf(elem)`
  ~ método que retorna o índice do elemento no vetor (ou -1)
  ~ `[5,6,7].indexOf(5) === 0`
  ~ `[5,6,7].indexOf(2) === -1`

---
<!-- {"hash": "metodos-comuns-de-vetores-3"} -->
## **Métodos** comuns de **vetores** (3/3)

`vetor.reverse()`
  ~ método que inverte a ordem dos elementos
  ~ `[1,2,3].reverse() === [3,2,1]`

`vetor.sort()`
  ~ método que coloca os elementos em ordem
  ~ `[8,1,-6].sort() === [-6,1,8]`
  ~ `['f', 'b'].sort() === ['b', 'f']`

`vetor.join(spacer)`
  ~ método que retorna uma string juntando os elementos
  ~ `['fl', 'rb'].join(' ') === 'fl rb'`
  ~ `['fl', 'rb'].join('+') === 'fl+rb'`

- [Lista de métodos comuns de vetores na MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)

---
<!-- {"layout": "2-column-content", "classes": "compact-code-more"} -->
## Exemplos com métodos de vetores (1/2)

- Função que soma todos os elementos do vetor <!-- {ul:.bulleted} -->
  ```js
  function soma(valores) {
    let total = 0;
    for (let n of valores) {
      total += n;
    }
    return total;
  }
  ```
- Função que retorna um vetor com os quadrados
  ```js
  function quadrados(valores) {
    let resultado = [];
    for (let n of valores) {
      resultado.push(n ** 2);
    }
    return resultado;
  }
  ```

1. Função que busca por um elemento específico <!-- {ol:.bulleted} -->
   ```js
   function busca(vetor, elem) {
     return vetor.indexOf(elem);
   }
   ```
1. Função que adiciona no vetor apenas se elemento ainda não estiver nele
   ```js
   function adicionaSemDuplicar(vetor, elem) {
     if (busca(vetor, elem) === -1) {
       vetor.push(elem);
     }
   }
   ```

---
<!-- {"classes": "compact-code-more"} -->
## Exemplos com métodos de vetores (2/2)

- Função que imprime uma matriz n x n de números <!-- {ul:.full-width.bulleted} --> ([no jsfiddle](https://jsfiddle.net/fegemo/f0uc4qyx/)) <!-- {target="_blank"} -->
- <!-- {.code-split-2} -->
  ```js
  function imprimeMatriz(matriz) {
    let resultado = '';
  ```
  ```js
  
  
  ```
- <!-- {.code-split-2} -->
  ```js
    for (let i = 0; i < matriz.length; i++) {
      resultado += '| ';
      for (let j = 0; j < matriz[i].length; j++) {
  ```
  ```js
  // 1. para cada linha
  // começou a linha
  // 2. para cada coluna
  ```
- <!-- {.code-split-2} -->
  ```js
        resultado += matriz[i][j] + ' ';
      }
      resultado += '|\n';
    }
  ```
  ```js
  // 3. imprime o elemento (i,j)

  // acabou a linha, coloca paredinha |
  
  ```
- <!-- {.code-split-2} -->
  ```js
    console.log(resultado);
  }
  ```
  ```js
  // e quebra linha \n

  ```
- <!-- {.code-split-2} -->
  ```js
  
  imprimeMatriz([[1,2],[3,4]])
  ```
  ```js
  // | 1 2 |
  // | 3 4 |
  ```


---
# Mais sobre funções

- Em JavaScript as **funções são super flexíveis**
  1. Função "tradicional" (já vimos)
  1. Função anônima (próximo slide)
  1. Função seta (próxima aula)
- Variáveis podem apontar para funções
- Podemos passar funções como parâmetro para outra função

---
<!-- {"layout": "2-column-content"} -->
## Função **anônima** (atribuída a **variável**)

1. Declaração de função "tradicional": <!-- {ol:.no-bullets} -->
   ```js
   function dizOla(nome) {
     console.log('olá ' + nome);
   }
   dizOla('submundo');
   ```
   - `function` + nome + (params)

- Criar uma **função <u>anônima</u>** e **atribuí-la a uma variável**: <!-- {ul:.no-bullets} -->
  ```js
  let dizOla = function(nome) {
    console.log('olá ' + nome);
  };
  dizOla('submundo');          
  ```
  - Funciona da mesma forma

---
## Passando **função como parâmetro**

- ```js
  function estudar(aluno, fnAprender) {
    console.log(aluno + ' aprendeu ' + fnAprender()); 
  }
  ```
  Vamos criar uma função que recebe outra como parâmetro →→→ <!-- {ul:.compact-code-more.bulleted} --> <!-- {li:.push-code-right} -->
- Ao chamar `estudar(...)` devemos passar uma função no segundo argumento <!-- {li:style="clear:both"} -->
- Neste exemplo, dependendo do que foi estudado, o aluno aprende coisas diferentes:
  ```js
  function lerHarryPotter() {                       function lerOlavoCarvalho() {
    return 'criatividade';                            return '?'; 
  }                                                 }
  let lerDarcyRibeiro = function() {
    return 'sociologia';
  }

  ```
- Agora vamos invocar a função `estudar(...)`:
  ```js
  estudar('André', lerHarryPotter);   // 'André aprendeu criatividade'
  estudar('Luiz', lerDarcyRibeiro);   // 'Luiz aprendeu sociologia'
  estudar('Jair', lerOlavoCarvalho);  // 'Jair aprendeu ?'
  ```

---
## Função vs Método

Função
~ sozinha no mundo, **ninguém é dono** dela
~ exemplo: todas as que vimos

Método
~ nasceu de algum objeto, ele **tem dono**
~ ex: as funções das strings, dos vetores (e outros)

- <!-- {ul:.full-width} -->
  <!-- {.code-split-2} -->
  ```js
  // 'dobra' é uma função
  function dobra(n) {
    return 2 * n;
  }
  let nota = 5;
  dobra(nota);
  ```
  ```js
  // sqrt() é método de Math
  nota = Math.sqrt(25);

  // toLowerCase() é método
  // das strings
  'HaNa MonTAna'.toLowerCase();
  ```

---
<!-- {"hash": "metodos-comuns-de-strings-1"} -->
## **Métodos** comuns de **strings** (1/3)

Toda string possui vários métodos diferentes que podemos invocar

`texto.length`
  ~ não é um método, mas retorna quantos caracteres
  ~ `'trem'.length === 4`

`texto[i]`
  ~ não é um método, mas retorna o i-ésimo caractere
  ~ `'trem'[3] === 'm'`

`texto.toLowerCase()`
  ~ método que retorna tudo em minúsculas
  ~ `'Doug'.toLowerCase() === 'doug'`

`texto.toUpperCase()`
  ~ método que retorna tudo em maiúsculas
  ~ `'Doug'.toUpperCase() === 'DOUG'`
  
---
<!-- {"hash": "metodos-comuns-de-strings-2"} -->
## **Métodos** comuns de **strings** (2/3)

`texto.trim()`
  ~ método que remove espaços em branco ao redor
  ~ `' mosca  '.trim() === 'mosca'`

`t.indexOf(trecho)`
  ~ método que retorna a posição do `trecho` no `texto` (ou -1)
  ~ `'Thanos'.indexOf('os') === 4`

`t.substr(ini, tam)`
  ~ método que retorna um trecho dado início e tamanho
  ~ `'Pronto'.substr(0, 2) === 'Pr'`

`t.includes(trecho)`
  ~ método que verifica se texto contém o trecho
  ~ `'Hakuna'.includes('ku') === true`
  
`t.split(separad)`
  ~ método que retorna um vetor de trechos
  ~ `'Banana'.split('a') === ['B', 'n', 'n']`

---
<!-- {"hash": "metodos-comuns-de-strings-3"} -->
## **Métodos** comuns de **strings** (3/3)

`t.startsWith(trech)`
  ~ método que verifica se começa com o trecho
  ~ `'Hakuna'.startsWith('Ha') === true`

`t.endsWith(trecho)`
  ~ método que verifica se termina com o trecho
  ~ `'Hakuna'.endsWith('na') === true`

`t.replace(tr, novo)`
  ~ método que substitui um trecho por algo novo
  ~ (apenas primeira ocorrência)
  ~ `'ana'.replace('a', 'e') === 'ena'`

`t.replaceAll(tr, n)`
  ~ método que substitui um trecho por algo novo
  ~ (todas as ocorrências)
  ~ `'ana'.replaceAll('a', 'e') === 'ene'` <!-- {dl:style="margin-bottom: 0"} -->

- [Lista de métodos de string na MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String) <!-- {ul:.no-margin} -->

---
<!-- {"layout": "2-column-content"} -->
## Exemplos que usam métodos de strings (1/2)

- Função que verifica se nome tem menos que 10 caracteres <!-- {ul:.bulleted.compact-code-more} -->
  ```js
  function temMenosDe10(nome) {
    return nome.length < 10;
  }
  temMenosDe10('Donarudo Torampu');
  // false
  ```
- Função que verifica se primeiro nome tem menos que 10 caracteres
  ```js
  function primeiroNomeMenos10(nome) {
    const cadaNomeSeparado = nome.split(' ');
    const primeiroNome = cadaNomeSeparado[0];
    return temMenosDe10(primeiroNome);
  }
  primeiroNomeMenos10('Donarudo Torampu');
  // true
  ```
1. Função que verifica se uma URL começa com https <!-- {ol:.bulleted.compact-code-more} -->
   ```js
   function comecaComHttps(url) {
     return url.startsWith('https');
   }
   comecaComHttps('http://omo.com.br');
   // false
   ```
1. Função que remove todas as ocorrências de um caractere em um texto
   ```js
   function removeCaractere(texto, caractere) {
     return texto.replaceAll(caractere, '');
   }
   ```

---
<!-- {"classes": "compact-code-more"} -->
## Exemplos que usam métodos de strings (2/2)

- Pega uma frase e se a última letra de cada palavra (com mais do que 1 letra) terminar em 'a' ou 'o', substitui por 'x' <!-- {ul:.bulleted} -->
  ([no jsfiddle](https://jsfiddle.net/fegemo/Lgwv6yne/)) <!-- {target="_blank"} -->
- <!-- {.code-split-2} -->
  ```js
  function alteraFinalzinhoPalavras(frase) {
    let palavras = frase.split(' ');
  ```
  ```js

  // 1. divide a frase em um vetor de palavras
  ```
- <!-- {.code-split-2} -->
  ```js
    for (let i = 0; i < palavras.length; i++) {
      palavras[i] = palavras[i].trim();
  ```
  ```js
  // 2. para cada palavra
  // 2.1. remove espaços em branco ao redor da palavra
  ```
- <!-- {.code-split-2} -->
  ```js
      if (palavras[i].length <= 1) continue;
  ```
  ```js
  // 2.1. verifica se tamanho > 1
  ```
- <!-- {.code-split-2} -->
  ```js
      if (palavras[i].endsWith('o') || 
          palavras[i].endsWith('a')) {
        const ateUltimaLetra = palavras[i].length - 1;
        
        palavras[i] = 
          palavras[i].substr(0, ateUltimaLetra) + 'x';
      }
    }
  ```
  ```js
  // 2.2. verifica se termina 'a' ou 'o'

  // 2.2.1. pega posição antes da última letra

  // 2.2.2. substitui última letra da palavra por 'x'



  ```
- <!-- {.code-split-2} -->
  ```js
    return palavras.join(' '); 
  }
  ```
  ```js
  // remonta a frase, juntando o vetor de palavras
  // colocando um espaço entre cada uma
  ```



---
<!-- {"layout": "centered"} -->
# Referências

1. Capítulo 2 do livro "JavaScript: The Good Parts"
1. Mozilla Developer Network (MDN)

