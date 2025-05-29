```
image_as_matrix()
```

現在の画像の状態をARGB32の配列として返します。

幅50、高さ30の行列 => 30行50列のテーブル

```julia
using Luxor, Images

Drawing(50, 50, :png)
origin()
background(randomhue()...)
sethue("white")
fontsize(40)
fontface("Georgia")
text("42", halign=:center, valign=:middle)
mat = image_as_matrix()
finish()
```
