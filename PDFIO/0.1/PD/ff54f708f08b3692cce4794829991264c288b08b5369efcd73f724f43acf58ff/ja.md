```
    pdOutlineItemGetAttr(item::PDOutlineItem) -> Dict{Symbol, Any}
```

`PDOutlineItem`オブジェクトに保存されている属性。`Prev`、`Next`、`First`、`Last`、および`Parent`のようなトラバーサルパラメータは、構造体と共に保存されます。

返される辞書オブジェクトには以下のキーが保存されています：

  * `:Title` - アイテムに割り当てられたタイトル（目次に表示されます）
  * `:Count` - アウトラインアイテムの下に開いているアイテムの数の表現。詳細についてはPDF Spec 32000-2008のセクション12.3.2.2を参照してください。主にユーザーインターフェースでのレンダリングに使用されます。
  * `:Destination` - `(filepath, PDDestination)`値。ファイルパスは、宛先が同じPDFファイル内の位置を指す場合は空の文字列です。このパラメータは、PDF仕様の`/Dest`と`/A`属性の組み合わせです。アクション要素が分析され、データが抽出され、最終的に参照される位置として`PDDestination`に保存されます。
  * `:C` - `DeviceRGB`空間におけるアウトラインの色。
  * `:F` - タイトルテキストレンダリングのフラグ `italic=1`、`bold=2`

# 例

```
    julia> pdOutlineItemGetAttr(outlineitem)
Dict{Symbol,Any} with 5 entries:
  :F           => 0x00
  :Title       => "Table of Contents"
  :Count       => 0
  :Destination => ("", PDDestination(2, /XYZ, Float32[0.0, 0.0, 0.0, 756.0], 0.0))
  :C           => Float32[0.0, 0.0, 0.0]
```
