```
ImageToTensor()
```

`(height, width, ...)` のサイズを持つ `Image{N, T}` を `(width, height, ..., ch)` のサイズを持つ `ArrayItem{N+1}` に展開します。ここで `ch` は `T` の色チャネルの数です。

`apply!` をサポートしています。

## 例

{cell=ImageToTensor}

```julia
using DataAugmentation, Images

h, w = 40, 50
image = Image(rand(RGB, h, w))
tfm = ImageToTensor()
apply(tfm, image) # サイズ (50, 40, 3) の WHC 形式の ArrayItem
```
