```
DrawImageMask(image)
```

画像の上にマスクを描画するためのインタラクティブなウィジェットです。

# 例

```julia
# ノートブックセル 1
using WebToys, FileIO
my_image = load("./path/to/image.png")
mask_widget = DrawImageMask(my_image)

# ノートブックセル 2
# このセルを実行する前にノートブックの出力で画像の上に描画します。
masked_image = my_image .* getmask(mask_widget)
```
