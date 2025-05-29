```
    Matching <: AbstractHistogramAdjustmentAlgorithm
    Matching(targetimg; nbins = 256, edges = nothing)

    adjust_histogram([T,] img, f::Matching)
    adjust_histogram!([out,] img, f::Matching)
```

`nbins`のビン数の粒度でヒストグラムが一致した画像を返します。最初の引数`img`は一致させる画像であり、`Matching()`の引数`targetimg`は一致させるための望ましいヒストグラムを持つ画像です。

# 詳細

ヒストグラムマッチングの目的は、ソース画像の強度を変換して、指定されたターゲット画像のヒストグラムに従って強度が分布するようにすることです。ヒストグラムを確率密度関数の区分定数モデルとして解釈すると（[`build_histogram`](@ref build_histogram(::AbstractArray, ::Integer, ::Union{Real,AbstractGray}, ::Union{Real,AbstractGray}))を参照）、ヒストグラムマッチングのタスクは、1つの確率分布を別のものに変換する問題としてモデル化できます[1]。この変換問題の解決策は、ソースとターゲットの確率密度関数の累積分布関数および逆累積分布関数を含むことがわかります。

特に、ランダム変数$x \thicksim p_{x}$と$z \thicksim p_{z}$は、それぞれソース画像とターゲット画像の強度を表し、次のように定義します。

$$
 S(x) = \int_0^{x}p_{x}(w)\mathrm{d} w \quad \text{および} \quad
 T(z) = \int_0^{z}p_{z}(w)\mathrm{d} w
$$

それぞれの累積分布関数を表します。次に、$Q(x) \thicksim p_{z}$となるようなマッピング$Q(\cdot)$は次のように与えられます。

$$
Q(x) =  T^{-1}\left( S(x) \right),
$$

ここで、$T^{-1}(y) = \operatorname{min} \{ x \in \mathbb{R} : y \leq T(x) \}$は$T(x)$の逆累積分布関数です。

このマッピングは、ヒストグラムマッチングをソース画像とターゲット画像のヒストグラム均等化を行い、2つの均等化されたヒストグラムを関連付けるものとして概念化できることを示唆しています。ヒストグラム均等化の詳細については、[`adjust_histogram`](@ref adjust_histogram(::Equalization, ::AbstractArray, ::Integer, ::Union{Real,AbstractGray}, ::Union{Real,AbstractGray}))を参照してください。

# オプション

`adjust_histogram`関数および`Matching`型のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img`と`targetimg`の選択肢

`adjust_histogram(img, Matching())`関数は、さまざまな入力タイプを処理できます。返される画像の型は入力型と一致します。

カラー画像の場合、入力は[YIQ](https://en.wikipedia.org/wiki/YIQ)型に変換され、Yチャネルの分布が一致します。修正されたYチャネルはIおよびQチャネルと組み合わされ、結果の画像は入力と同じ型に変換されます。

## `nbins`の選択肢

ヒストグラムのビンの総数を指定できます。ビンの数を指定しない場合、デフォルト値の256ビンが使用されます。

## `edges`の選択肢

ビンの数を指定しない場合、`AbstractRange`型を指定することで、区間の分割方法を直接指定するオプションがあります。

# 例

```julia
using Images, TestImages, ImageView

img_source = testimage("mandril_gray")
img_target = adjust_histogram(img_source, GammaCorrection(gamma = 0.5))
img_transformed = adjust_histogram(img_source, Matching(targetimg = img_target))
#=
    目視検査により、img_transformedがimg_sourceよりも
    img_targetに非常に近いことが確認されます。
=#
imshow(img_source)
imshow(img_target)
imshow(img_transformed)
```

# 参考文献

1. W. Burger and M. J. Burge. *Digital Image Processing*. Texts in Computer Science, 2016. [doi:10.1007/978-1-4471-6684-9](https://doi.org/10.1007/978-1-4471-6684-9)

```
