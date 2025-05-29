```
Varspec
```

変数に関するすべての関連情報を保持する構造体。 フィールドは次のとおりです。

  * name: 変数の名前
  * storagetype: 変数のJulia型
  * conversionfcie: 生の文字列値をJulia型に変換するためのJulia関数、読み取りに使用
  * dumpfcie: Julia型を固定幅の文字列に変換するためのJulia関数、書き込みに使用
  * startpos: レコード内の変数の開始位置
  * length: 変数のバイト数

定義済みの使用可能な型は、文字列変数用の `InlineStringXX` 型、整数変数用の `Union{Missing,Int64}` および `IntXX`、実数用の `FloatXX`、スキップする必要がある変数用の `Nothing` です。 入力に別の型を使用したい場合は、バイト文字列を指定された型に変換する関数を指定する必要があります。

固定幅ファイルに書き込むには、使用される型の変換関数が利用可能でなければなりません。 `String`、`Union{Missing,Int64}`、`Float64` および `Nothing` 用の定義済み関数が定義されています。
