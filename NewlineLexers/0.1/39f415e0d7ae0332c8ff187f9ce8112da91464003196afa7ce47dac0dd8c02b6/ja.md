```
Lexer{E,OQ,CQ,NL,IO_t}

Lexer(io, escapechar, openquotechar, closequotechar, newline) -> Lexer{E,OQ,CQ,NL,IO_t}
Lexer(io, nothing, newline) -> Lexer{Nothing,Nothing,Nothing,NL,IO_t}
```

改行検出のための状態を持つレキサータイプ。`find_newlines!`関数と一緒に使用します。型パラメータは次の通りです：

  * `E`: エスケープ文字
  * `OQ`: 開き引用符
  * `CQ`: 閉じ引用符
  * `NL`: 改行文字
  * `IO_t`: IOオブジェクトの型、例えば`IOBuffer`や`IOStream`

`E`、`OQ`、`CQ`のいずれかが`Nothing`であるか、すべてが単一バイト文字である必要があります。

`E`、`OQ`、`CQ`が`Nothing`でない場合、レキサーは入力内のすべての改行を見つけますが、それは文字列（2つの引用符の間）内にはありません。これは、CSVのレコードセパレーターを見つけるのに便利です。

すべてが`Nothing`の場合、レキサーは引用符を意識せず、文字列内にあるかどうかに関係なく、入力内のすべての改行を見つけます。そのようなレキサーは`Lexer(io, nothing, newline)`で構築できます。
