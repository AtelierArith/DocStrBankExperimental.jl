```
TextConfig

TextConfig(; kw...)
TextConfig(face, namepixels, namepos, timepixels, timepos, fcolor, bcolor)
```

画像にタイムステップとグリッド名を印刷するためのテキスト設定。

# 引数 / キーワード

  * `font`: 探すフォント名の `String`、または `FreeTypeAbstraction.FTFont`。`FTFont` はより迅速にロードされる可能性があります。
  * `namepixels` と `timepixels`: フォントのピクセルサイズ。
  * `timepos` と `namepos`: ラベルの位置を設定するタプル、`Int` ピクセル単位。
  * `fcolor` と `bcolor`: 前景色と背景色、`ARGB32` として。
