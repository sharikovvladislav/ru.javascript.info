# Найдите строки в кавычках

Создайте регулярное выражение для поиска строк в двойных кавычках `subject:"..."`.

Важно, что строки должны поддерживать экранирование с помощью обратного слеша, по аналогии со строками JavaScript. Например, кавычки могут быть вставлены как `subject:\"`, новая строка как `subject:\n`, а сам обратный слеш как `subject:\\`.

```js
let str = "Как вот \"здесь\".";
```

В частности, обратите внимание: двойная кавычка после обратного слеша `subject:\"` не оканчивает строку.

Поэтому мы должны искать от одной кавычки до другой, игнорируя встречающиеся экранированные кавычки. 

В этом и состоит основная сложность задачи, которая без этого условия была бы элементарной.

Примеры подходящих строк:
```js
.. *!*"test me"*/!* ..  
.. *!*"Скажи \"Привет\"!"*/!* ... (строка с экранированными кавычками)
.. *!*"\\"*/!* ..  (внутри двойной слеш)
.. *!*"\\ \""*/!* ..  (внутри двойной слеш и экранированная кавычка)
```

В JavaScript приходится удваивать обратные слеши, чтобы добавлять их в строку, как здесь:

```js run
let str = ' .. "test me" .. "Скажи \\"Привет\\"!" .. "\\\\ \\"" .. ';

// эта строка в памяти:
alert(str); //  .. "test me" .. "Скажи \"Привет\"!" .. "\\ \"" ..
```
