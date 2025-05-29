```
hist_matched_img = histmatch(img, oimg, nbins)
```

`nbins`のビン数でヒストグラムが一致した画像を返します。最初の引数`img`は一致させる画像で、2番目の引数`oimg`は一致させる対象のヒストグラムを持つ画像です。

# 詳細

ヒストグラムマッチングの目的は、ソース画像の強度を変換して、指定されたターゲット画像のヒストグラムに従って強度が分布するようにすることです。ヒストグラムを確率密度関数の区分定数モデルとして解釈すると（[imhist](@ref)を参照）、ヒストグラムマッチングのタスクは、ある確率分布を別のものに変換する問題としてモデル化できます[1]。この変換問題の解決策は、ソースおよびターゲットの確率密度関数の累積分布関数および逆累積分布関数を含むことがわかります。

特に、ランダム変数$x \thicksim p_{x}$と$z \thicksim p_{z}$はそれぞれソース画像とターゲット画像の強度を表し、次のように定義します。

$$
 S(x) = \int_0^{x}p_{x}(w)\mathrm{d} w \quad \text{および} \quad
 T(z) = \int_0^{z}p_{z}(w)\mathrm{d} w
$$

これらはそれぞれの累積分布関数を表します。求めるマッピング$Q(\cdot)$は、$Q(x) \thicksim p_{z}$となるように次のように与えられます。

$$
Q(x) =  T^{-1}\left( S(x) \right),
$$

ここで、$T^{-1}(y) = \operatorname{min} \{ x \in \mathbb{R} : y \leq T(x) \}$は$T(x)$の逆累積分布関数です。

このマッピングは、ヒストグラムマッチングをソース画像とターゲット画像のヒストグラム均等化を行い、2つの均等化されたヒストグラムを関連付けるものとして概念化できることを示唆しています。ヒストグラム均等化の詳細については[histeq](@ref)を参照してください。

# オプション

この関数のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img`と`oimg`の選択肢

`histmatch`関数はさまざまな入力タイプを処理できます。返される画像は入力タイプに依存します。入力が`Image`の場合、結果の画像は同じタイプで、同じプロパティを持ちます。

カラー画像の場合、入力は[YIQ](https://en.wikipedia.org/wiki/YIQ)タイプに変換され、Yチャネルはガンマ補正されます。これがIおよびQチャネルと組み合わされ、結果の画像は入力と同じタイプに変換されます。

## `nbins`の選択肢

ヒストグラムのビンの総数を指定できます。

# 例

```julia
using Images, TestImages, ImageView

img_source = testimage("mandril_gray")
img_target = adjust_gamma(img_source,1/2)
img_transformed = histmatch(img_source, img_target)
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

参照： [histeq](@ref)、[clahe](@ref)、および[imhist](@ref)。
