```
CellStyle(;
    bold::Bool = false,
    italic::Bool = false,
    underline::Bool = false,
    halign::Symbol = :center,
    valign::Symbol = :top,
    indent_pt::Float64 = 0.0,
    border_bottom::Bool = false,
    merge::Bool = false,
    mergegroup::UInt8 = 0,
)
```

`Cell`の視覚的な外観を決定する`CellStyle`オブジェクトを作成します。

キーワード引数:

  * `bold`が`true`の場合、テキストを`bold`でレンダリングします。
  * `italic`が`true`の場合、テキストを`italic`でレンダリングします。
  * `underline`が`true`の場合、テキストに下線を引きます。
  * `halign`は、セル内の水平揃えを決定します。`:left`、`:center`、または`:right`のいずれかです。
  * `valign`は、セル内の垂直揃えを決定します。`:top`、`:center`、または`:bottom`のいずれかです。
  * `indent_pt`は、セルテキストにポイント単位で左のインデントを追加します。
  * `border_bottom`が`true`の場合、セルに下部の境界線を追加します。
  * `merge`は、隣接するセルが`==`等しい場合、それらを単一のマージされたセルとしてレンダリングします。
  * `mergegroup`は、マージされるべきでない2つの等しい隣接セルグループを区別するために使用できる数値です。
