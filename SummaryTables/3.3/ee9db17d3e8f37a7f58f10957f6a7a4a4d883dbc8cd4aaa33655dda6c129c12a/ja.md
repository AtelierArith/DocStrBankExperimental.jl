```
Cell(value, style::CellStyle)
Cell(value; [bold, italic, underline, halign, valign, border_bottom, indent_pt, merge, mergegroup])
```

値 `value` と `CellStyle` `style` を持つ `Cell` を構築します。これはキーワード引数を使って暗黙的に作成することもできます。スタイリングオプションの説明については `CellStyle` を参照してください。値が `nothing` のセルは空のセルとして表示されます（スタイルは適用される場合があります）。`value` の型は何でも可能です。

特別な動作を持ついくつかの型は次のとおりです：

  * `Multiline` は、セル内で複数行に分かれたコンテンツのためのものです。このオブジェクトは他の値の中にネストして使用することはできず、最上位の値としてのみ使用できます。
  * `Concat` は、複数の値を `String` に補間することなく連結するためのもので、独自の特別な動作を保持します。
  * `Superscript` と `Subscript`
  * `Annotated` は、オプションの上付き文字ラベルと脚注注釈を持つ値のためのものです。
