```
GameHeaders
```

ゲームのPGNヘッダータグを表す型。

`event`、`site`、`date`、`round`、`white`、`black`、および`result`の7つの必須PGNタグそれぞれのスロットを含み、すべて文字列です。残りのタグは`othertags`スロットに含まれ、そこには`GameHeader`のベクターが含まれます。
