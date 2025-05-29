```
エラー
```

無効な補助データ値を読み込む際に返されるエラーを表す列挙型です。エラーは*非網羅的*であり、非破壊的なリリースで追加される可能性があります。

以下のエラーは、実際の値の代わりに`AbstractAuxiliary`に含まれる場合があります：

  * `InvalidTypeTag` (SAMのみ)：未知の型を持つ補助値
  * `InvalidArrayEltype` (SAMのみ)：未知の要素型を持つ`B`値
  * `InvalidInt` (SAMのみ)：`Int32`に解析できない整数
  * `InvalidFloat` (SAMのみ)：`Float32`に解析できない浮動小数点数
  * `InvalidChar`：`'!':'~'`にない`Char`の読み込み
  * `InvalidString`：`re"[ !-~]"`にない文字を含む文字列
  * `InvalidHex`：奇数の記号を持つ`H`値、または`re"[0-9A-F]"`にない記号
  * `InvalidArray`：不正な`B`値

参照：[`Errors`](@ref)
