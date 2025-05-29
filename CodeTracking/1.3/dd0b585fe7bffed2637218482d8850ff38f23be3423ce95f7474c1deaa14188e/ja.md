```
filepath, line = whereis(method::Method)
```

`method`の定義のファイルと行を返します。`line`の意味はJuliaのバージョンによって異なります：Julia 1.5以降では、これはメソッド宣言の行番号であり、それ以前のバージョンではメソッドの本体の最初の行です。
