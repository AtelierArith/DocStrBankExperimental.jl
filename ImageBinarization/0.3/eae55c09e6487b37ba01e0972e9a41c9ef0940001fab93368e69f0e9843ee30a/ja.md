```
AdaptiveThreshold <: AbstractImageBinarizationAlgorithm
AdaptiveThreshold([img]; [window_size,] percentage = 15)

binarize([T,] img, f::AdaptiveThreshold)
binarize!([out,] img, f::AdaptiveThreshold)
```

背景の照明に応じて変化する閾値を使用して `img` を二値化します。

# 出力

二値化された画像を `Array{Gray{T}}` として `size(img)` のサイズで返します。`T` が指定されていない場合、`out` と `img` から推測されます。

# 拡張ヘルプ

# 詳細

ピクセルの値が、ピクセルを中心とした $s \times s$ のピクセルの平均より `t` パーセント少ない場合、そのピクセルは黒に設定され、それ以外の場合は白に設定されます。

$$
s \times s
$$

の近傍の平均を計算するための計算効率の良い方法は、*積分画像* `integral_image` を使用することによって達成されます。

このアルゴリズムは、背景と前景のコントラストが明確に異なる画像で特に効果的です。詳細については [1] を参照してください。

# 引数

関数の引数については、以下でより詳細に説明します。

## `img::AbstractArray`

二値化する必要がある画像です。画像は自動的に `Gray` に変換され、必要なグレーレベルのヒストグラムが構築されます。

`img` を `AdaptiveThreshold` に渡すことで、「最適な」 `window_size` を自動的に推測することもできます。

# オプション

`AdaptiveThreshold`、`binarize` および `binarize!` のパラメータに関するさまざまなオプションについては、以下でより詳細に説明します。

## `percentage` の選択肢

`percentage` に整数を指定できます（[1] で `t` として示される）。これは 0 から 100 の間でなければなりません。デフォルト: 15

## `window_size` の選択肢

引数 `window_size`（[1] で `s` として示される）は、ゼロより大きいピクセルの正方形の近傍のサイズを指定します。

`img` が `AdaptiveThreshold` コンストラクタに渡されると、`window_size` は `img` の幅と高さの平均の 1/8 に最も近い整数として推測されます。

# 例

```julia
using TestImages

img = testimage("cameraman")
f = AdaptiveThreshold(window_size = 16)
img₀₁ = binarize(img, f)

f = AdaptiveThreshold(img) # `img` を使用して最適な `window_size` を推測
img₀₁ = binarize(img, f)
```

インプレース操作については [`binarize!`](@ref) も参照してください。

# 参考文献

[1] Bradley, D. (2007). Adaptive Thresholding using Integral Image. *Journal of Graphic Tools*, 12(2), pp.13-21. [doi:10.1080/2151237x.2007.10129236](https://doi.org/10.1080/2151237x.2007.10129236) ```
