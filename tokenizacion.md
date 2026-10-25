## 1. El problema

Las personas escribimos texto, pero los modelos de IA procesan datos numéricos. Para conectar ambos mundos, se utiliza un **tokenizador (tokenizer)**, que divide el texto en unidades llamadas tokens y les asigna identificadores numéricos.

Proceso general:

`Texto → Tokens → IDs de tokens`

Ejemplo ilustrativo:

- Texto: `El gato duerme.`
- Tokens: `["El", " gato", " duerme", "."]`
- IDs: `[42, 817, 1294, 9]`

Los números son ficticios y dependen del vocabulario de cada tokenizador.

## 2. ¿Qué es un token?

Un **token** es una unidad de texto que el tokenizador reconoce.

Un token no equivale necesariamente a una palabra completa. Puede ser:

- Una palabra completa.
- Una parte de una palabra.
- Un carácter o una combinación de caracteres.
- Un signo de puntuación.
- Una unidad que incluye espacios.

Ejemplo hipotético:

`gatito → ["gat", "ito"]`

La división exacta depende del tokenizador utilizado.

## 3. ¿Por qué no utilizar una palabra por token?

Un vocabulario que contenga una entrada para cada palabra posible tendría problemas:

- Existen muchísimas palabras y nombres propios.
- Aparecen palabras nuevas y errores de escritura.
- Sería difícil cubrir todas las combinaciones posibles.
- Un vocabulario demasiado grande puede resultar poco práctico.

Por eso, muchos modelos utilizan unidades subléxicas: partes de palabras o combinaciones frecuentes de caracteres.

Esto permite representar palabras desconocidas combinando unidades más pequeñas, siempre que el tokenizador pueda descomponerlas de esa manera.

## 4. ¿Cómo se construye un vocabulario de tokens?

Un método conocido es **BPE (Byte Pair Encoding)**.

Su funcionamiento simplificado es:

1. Se parte de unidades pequeñas del texto.
2. Se identifican combinaciones frecuentes.
3. Se fusionan determinadas unidades para formar otras mayores.
4. Se repite el proceso hasta obtener un vocabulario adecuado.

Por ejemplo, combinaciones frecuentes de caracteres pueden terminar representándose mediante un único token.

BPE tiene distintas variantes y no es el único método de tokenización.

Generalmente, el tokenizador se construye antes del entrenamiento del modelo lingüístico principal. Durante su uso, aplica las reglas y el vocabulario que ya tiene establecidos.

## 5. ¿Qué es un ID de token?

Un **ID de token** es un número que identifica una unidad concreta dentro del vocabulario del tokenizador.

Ejemplo:

| Token | ID ilustrativo |
|---|---:|
| `gato` | 100 |
| `perro` | 101 |
| `casa` | 102 |

Estos números funcionan como identificadores. No representan directamente el significado de las palabras ni indican que una palabra sea más importante que otra.

Cada vocabulario puede asignar IDs diferentes a los mismos tokens.

## 6. Conceptos fundamentales

- **Texto:** la secuencia de caracteres escrita por una persona.
- **Tokenización:** el proceso de dividir el texto en tokens.
- **Token:** una unidad de texto reconocida por el tokenizador.
- **Vocabulario:** el conjunto de tokens que puede reconocer el tokenizador.
- **ID de token:** el número que identifica un token dentro de ese vocabulario.
- **BPE:** un método que construye unidades mayores mediante la fusión de unidades frecuentes.

## 7. Esquema general

`Texto → Tokenizador → Tokens → IDs numéricos`

Este proceso convierte el texto en una representación que puede utilizarse como entrada de un modelo de lenguaje.

Sin embargo, los IDs todavía no son embeddings. Para comprender cómo el modelo procesa matemáticamente el texto, el siguiente paso es estudiar cómo esos identificadores se transforman en vectores numéricos.

## Idea clave

**Un token no es necesariamente una palabra, y su ID no es su significado.** La tokenización transforma el texto en unidades identificables; las etapas posteriores del modelo realizan las operaciones matemáticas necesarias para procesar esas unidades.
