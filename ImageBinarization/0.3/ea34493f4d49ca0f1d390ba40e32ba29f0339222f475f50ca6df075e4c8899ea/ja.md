```
Niblack <: AbstractImageBinarizationAlgorithm
Niblack(; window_size = 7, bias = 0.2)

binarize([T,] img, f::Niblack)
binarize!([out,] img, f::Niblack)
```

テキスト画像であるという仮定の下、Niblack適応しきい値処理 [1] を適用します。

# 出力

バイナライズされた画像を `Array{Gray{T}}` のサイズ `size(img)` として返します。`T` が指定されていない場合、`out` と `img` から推測されます。

# 拡張ヘルプ

# 詳細

入力画像は、Niblackのアルゴリズム [2] の修正版を使用して、画像全体でしきい値を変化させることによってバイナライズされます。各ピクセルのしきい値 $T$ は、その周囲の隣接ピクセルの強度の平均 $m$ と標準偏差 $s$ に基づいて定義されます。このしきい値は次のように与えられます。

$$
T(x,y) = m(x,y) + k \cdot s(x,y),
$$

ここで $k$ は、標準偏差が $T$ の値に与える影響を重み付けするユーザー定義のパラメータです。

Niblackのアルゴリズムは、背景ピクセルの灰色値の変動に非常に敏感であり、これがしばしばローカルしきい値を超え、バイナライズされた画像にアーティファクトとして現れることに注意してください。このパッケージに含まれる [`Sauvola`](@ref) アルゴリズムは、この問題に対処しようとする試みを実装しています [2]。

# 引数

## `img`

背景 (0) と前景 (1) ピクセル値に対して、ピクセルごとの適応しきい値に従ってバイナライズされる画像。

## `bias::Real`  (出版物での $k$ に相当)

しきい値に対するユーザー定義のバイアスパラメータ。負の値を取ることができます。大きな `bias` は出力における黒いピクセルを増加させます。

## `window_size::Integer` (出版物での $w$ に相当)

各ピクセルのしきい値は、その周囲のすべての隣接ピクセルの強度の分布の関数です。このウィンドウの辺の長さは $2w + 1$ で、ターゲットピクセルは中央の位置にあります。

指定されていない場合、`window_size` は `7` です。

# 例

`TestImages` パッケージの "cameraman" 画像をバイナライズします。

```julia
using TestImages, ImageBinarization

img = testimage("cameraman")
img₀₁ = binarize(img, Niblack())
```

# 参考文献

[1] Wayne Niblack (1986). *An Introduction to Image Processing*. Prentice-Hall, Englewood Cliffs, NJ: 115-16. [2] J. Sauvola and M. Pietikäinen (2000). "Adaptive document image binarization". *Pattern Recognition* 33 (2): 225-236. [doi:10.1016/S0031-3203(99)00055-2](https://doi.org/10.1016/S0031-3203(99)00055-2)
