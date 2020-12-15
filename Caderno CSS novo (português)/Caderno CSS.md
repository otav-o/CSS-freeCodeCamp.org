### Aula 1: Inserindo CSS na página HTML

- Externo

  - Possível de usar em mais de uma página, mais fácil de editar

  - ```html
    <link rel='stylesheet' href='estilos.css'>
    ```

- Incorporado: tag `<style>`

  - Só vale para a página

- Inline: na tag que receberá o estilo

  - ```html
    <body style="background-color: #0f0">
    ```

- Seletor:
  - `body { }`
  - Comandos na forma `propriedade: valor`

```css
body {
    background-color: #f00;
}
```

- Ordem de prioridade: inline > incorporado > externo

---

### Aula 2 - Seletores

- Seletor de tags

```css
p { color: red; }
```

- Seletor de ids: jogo da velha `#`

```css
#p1 {
	font-size: 20pt;
}
```

- Seletor de classes: ponto `.`

```css
.txt {
	color: green;
}
```

- Grupo de seletores: separar por vírgula

```css
p, h1, h4, h5, h6 {
	color: blue;
    font-weight: lighter;
}
```

- Classe serve para mais de um elemento. Id só deve ser inserido em uma tag.

- Hierarquia: **formatação por id > classe > tag**

```html
<h1 class='titulo'> ... </h1>

<p id='texto'> ... </p>
```

---

### Aula 3 - Cores

- Padrões: hexadecimal e decimal

#### Hexadecimal

#FF0000 = #F00 (forma resumida)

- O padrão hexadecimal tem base 16, sendo 0 a 9 e A até F
- Cada par indica a cor vermelha, verde e azul: RRGGBB
- Só usa forma resumida quando os algarismos dos pares são iguais

#### Decimal

- Ex.: `rgb (205, 71, 102)`
- 0 a 255

---

### Aula 4 - Background (parte 1)

#### background-image

```css
body {
    background-image: url(img/foto.jpg);
}
```

#### background-size

- Caso seja usado apenas um valor, aplica à largura sem distorcer.

```css
body {
    
    background-color: black;
    background-size: 200px;
    background-size: 400px 50px; /*largura, algura*/
    /*aplica-se ao fundo, e não à imagem!*/
    background-repeat: repeat-x;
    background-repeat: repeat-y;
    background-repeat: repeat; /*(padrão)*/
    background-repeat: no-repeat;
    
    background-position: right top;
    /*left bottom, etc*/
    
    background-position: 200px 0px; /*horizontal (x), vertical (y)*/
    
}
```

- Se não configurar, a imagem irá se repetir por toda a página

```css
p {
    font-size: 30pt;
	color: #fff;
    
	background-image: url(marcador.png), url(logo.jpg); 
    
    /*é possível adicionar em um parágrafo*/
	/*também tem como ter mais de uma imagem no fundo. Aí tem que separar os demais estilos por vírgula*/
	
	
    
	background-repeat: repeat-x, no-repeat;
	background-position: 0px 8px, 100px 100px;
    background-size: 500px;
	
}
```

---

### Aula 5 - Background (parte 2)

- Ver o código desta aula! Fica mais fácil

#### background-clip

- Propriedade que especifica onde o fundo vai iniciar.
- **`border-box`**: a borda faz parte do background
  - Colocando a borda pontilhada (dotted) é possível ver que o fundo continua atrás dela.
- **`padding-box`**: não considera a área da borda no background
- **`content-box`**: o fundo só existe onde há conteúdo
  - Ex.: uma `<div>` que possui texto não teria fundo nela inteira, apenas na linha do texto
- *Todos esses valores são da propriedade background-clip e podem ser usados para qualquer tag*

#### border

- Meta-propriedade que inclui outras 3 propriedades de formatação de borda
  - Espessura da linha, tipo de linha e cor
  - `border: [espessura][tipo][cor]`
    - tipo (ex.): solid, dotted

#### padding

- Margem interna do elemento, **Separa a borda do conteúdo**
- Um valor só: considera os 4 lados
  - `padding: 50px;`
- Quatro valores: **topo, direita, baixo, esquerda (sentido horário**)
  - `padding: 0px 10px 50px 10px;`
- Pode acabar aumentando o elemento (e seu background) 

```html
<div id='d1'></div>
<div id='d2'></div>
<div id='d3'></div>
```

```css
#d1, #d2, #d3 {
	border: 10px dotted #000;
	padding: 35px; 
}
#d1 {
    background-clip: border-box; /*valor padrão*/
}
```

![image-20201211111858198](image-20201211111858198.png)

---

### Aula 6 - Background (parte 3)

#### background-attachment

- Rolagem da imagem de fundo (fixa ou movimentando com o conteúdo)
- Configurar uma imagem que se ajuste ao tamanho da tela
- valor padrão:
  - `background-attachment: scroll;`

```css
body {
	background-image: url(logo.jpg), url(marcador.png);
	background-repeat: no-repeat, repeat;
	
	background-size: 400px, 30px;
    background-attachment: scroll, fixed; 
}
```

- lembrar que background não é exclusivo de `<body>`

---

### Aula 7 - Background (parte 4)

#### Metapropriedade background

- Configuração de várias propriedades em apenas uma

```css
body {
    background: #AAA url(folha.jpg) repeat-x 10px 0px / 200px;
    /*cor, imagem, repetição, posição de início da imagem, tamanho (colocar barra antes. Pode ser em porcentagem também - aí ajusta à janela)*/
    
    background-color: #fff;
    background-image: url(folha.jpg);
    background-repeat: no-repeat;
    background-position: center, 0px; /*center ou 50%*/
}
```

- Parece que a ordem não faz diferença 

---

### Aula 8 - Border

- border-style, border-color, border-width
- 