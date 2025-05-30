```
Sauvola <: AbstractImageBinarizationAlgorithm
Sauvola(; bias = 0.2, window_size=7)

binarize([T,] img, f::Sauvola)
binarize!([out,] img, f::Sauvola)
```

テキスト画像であると仮定して、Sauvola–Pietikäinen適応画像二値化[1]を適用します。

# 出力

二値化された画像を`Array{Gray{T}}`のサイズ`size(img)`として返します。`T`が指定されていない場合、`out`と`img`から推測されます。

# 拡張ヘルプ

# 詳細

入力画像は、周囲のピクセルの強度の平均$m$と標準偏差$s$に基づいて、画像全体でしきい値を変化させることによって二値化されます。これはNiblackのアルゴリズム[2]の修正版を使用しています。Niblackのアプローチは、周囲のピクセルの強度の平均$m$と標準偏差$s$に基づいて、各ピクセルのしきい値$T$を定義することでした。

$$
T(x,y) = m(x,y) + k \cdot s(x,y),
$$

ここで、$k$は標準偏差が$T$の値に与える影響を重み付けするユーザー定義のパラメータです。

Niblackのアルゴリズムは、背景ピクセルの灰色値の変動に非常に敏感であり、しばしばローカルしきい値を超えて二値化された画像にアーティファクトとして現れます。SauvolaとPietikäinen[1]は、標準偏差の動的範囲$R$（すなわち、色空間におけるその最大可能値）を導入し、しきい値は次のように与えられます。

$$
T(x,y) = m(x,y) \cdot \left[ 1 + k \cdot \left( \frac{s(x,y)}{R} - 1 \right) \right]
$$

これにより、標準偏差が$T$の値に与える寄与が適応的に増幅されます。

Sauvola–Pietikäinenアルゴリズムは、Shafait、Keysers、Breuel[3]によって提案された最適化を使用してここに実装されており、積分画像を使用して各ピクセルの$m$と$s$の値を定数時間で計算します。これらのデータ構造はすべてソース画像を一度通過させることで計算できるため、実行時間が大幅に改善されます。

# 引数

## `img`

背景（0）と前景（1）ピクセル値に対して、ピクセルごとの適応しきい値に従って二値化される画像です。

## `window_size::Integer`（出版物で$w$と表記）

各ピクセルのしきい値は、その周囲のすべての隣接ピクセルの強度の分布の関数です。このウィンドウの辺の長さは$2w + 1$で、ターゲットピクセルは中央の位置にあります。

## `bias::Real`（出版物で$k$と表記）

ユーザー定義のバイアスパラメータです。負の値を取ることもできますが、典型的には[0.2, 0.5]の範囲の値です。[1]によれば、このアルゴリズムは$k$の値に対してそれほど敏感ではありません。

# 例

`TestImages`パッケージの「カメラマン」画像を二値化します。

```julia
using TestImages, ImageBinarization

img = testimage("cameraman")
img_binary = binarize(img, Sauvola(window_size = 9, bias = 0.2))
```

# 参考文献

1. J. Sauvola and M. Pietikäinen (2000). "Adaptive document image binarization". *Pattern Recognition* 33 (2): 225-236. [doi:10.1016/S0031-3203(99)00055-2](https://doi.org/10.1016/S0031-3203(99)00055-2)
2. Wayne Niblack (1986). *An Introduction to Image Processing*. Prentice-Hall, Englewood Cliffs, NJ: 115-16.
3. Faisal Shafait, Daniel Keysers and Thomas M. Breuel (2008). "Efficient implementation of local adaptive thresholding techniques using integral images". Proc. SPIE 6815, Document Recognition and Retrieval XV, 681510 (28 January 2008). [doi:10.1117/12.767755](https://doi.org/10.1117/12.767755)

```
