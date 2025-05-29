imgradients(img, kernelfun=KernelFactors.ando3, border="replicate") -> gimg1, gimg2, ...

`img`のすべての点において、`kernelfun`で指定されたカーネルを使用して、1次元目と2次元目の方向の勾配を推定します。

入力の各次元に対して1つの配列からなるタプル`(gimg1, gimg2, ...)`を返します：`gimg1`は1次元目に関する導関数に対応し、`gimg2`は2次元目に対応し、以下同様です。

## 例

```julia
using Images, ImageFiltering, TestImages
img = testimage("mandrill")
imgr = imgradients(img, KernelFactors.sobel, "reflect")
mosaicview(imgr...)
```
