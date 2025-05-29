```
    MidwayEqualization <: AbstractHistogramAdjustmentAlgorithm
    MidwayEqualization(; nbins = 256, minval = 0, maxval = 1)

    adjust_histogram([T,] img_sequence, f::MidwayEqualization(nbins = 256, edges = nothing))
    adjust_histogram!([out_sequence,] img_sequence, f::MidwayEqualization(nbins = 256, edges = nothing))
```

2つの画像に同じヒストグラムを与えつつ、できるだけ以前のグレー階調のダイナミクスを維持します。

# 詳細

ミッドウェイヒストグラム均等化の目的は、2つの画像の強度を変換して、強度が共通の「ミッドウェイ」分布に従って分布するようにすることです。共通分布を表すヒストグラムは、画像の元のグレー階調のダイナミクスができるだけ保存されるように選ばれます。ヒストグラムを確率密度関数の区分定数モデルとして解釈すると（[`build_histogram`](@ref build_histogram(::AbstractArray, ::Integer, ::Union{Real,AbstractGray}, ::Union{Real,AbstractGray})))を参照）、ミッドウェイヒストグラム均等化のタスクは、1つの確率分布を別のものに変換する問題としてモデル化できます（[`adjust_histogram`](@ref adjust_histogram(::Matching,::AbstractArray, ::AbstractArray, ::Integer)))を参照）。この変換問題の解決策は、ソースと「ミッドウェイ」確率密度関数の累積分布関数および逆累積分布関数を含むことがわかります。特に、確率変数 $X_i \thicksim p_{x_i} \; (i = 1,2)$、および $Z \thicksim p_{z}$ はそれぞれ最初の、2番目の、そして「ミッドウェイ」画像の強度を表し、次のように定義されます。

$$
 S_{X_i}(x) = \int_0^{x}p_{x_i}(w)\mathrm{d} w \; \quad \text{および} \quad
 T_{Z}(x) = \frac{2}{\frac{1}{S_{X_1}(x)} + \frac{1}{S_{X_2}(x)}}
$$

これは、2つの入力画像の累積分布関数とその*調和平均*を表します。次に、求められるマッピング $Q_{X_i}(\cdot)$ $(i = 1,2)$ は、$Q_{X_i}(x) \thicksim p_{z}$ となるように次のように与えられます。

$$
Q_{X_i}(x) =  T_{Z}^{-1}\left( S_{X_i}(x) \right),
$$

ここで、$T_{Z}^{-1}(y) = \operatorname{min} \{ x \in \mathbb{R} : y \leq T_{Z}(x) \}$ は $T_{Z}(x)$ の逆累積分布関数です。

# オプション

`adjust_histogram` 関数および `MidwayEqualization` タイプのパラメータに関するさまざまなオプションが以下に詳述されています。

## `img_sequence` の選択肢

`adjust_histogram` 関数は、長さ2の画像の `Vector`（画像のペア）を期待し、修正された画像の長さ2の `Vector` を返します。この関数はさまざまな入力タイプを処理できます。返される画像のタイプは入力タイプと一致します。

カラー画像の場合、入力は [YIQ](https://en.wikipedia.org/wiki/YIQ) タイプに変換され、Yチャネルの分布は「ミッドウェイ」分布に従って変換されます。修正されたYチャネルはIおよびQチャネルと組み合わされ、結果として得られる画像は入力と同じタイプに変換されます。

## `nbins` の選択肢

ヒストグラムの総ビン数を指定できます。ビン数を指定しない場合は、デフォルト値の256ビンが使用されます。

## `edges` の選択肢

ビン数を指定しない場合、`AbstractRange` タイプを指定することで、区間の分割方法を直接指定するオプションがあります。

# 例

```julia
using Images, TestImages, ImageView, ImageContrastAdjustment

img = testimage("mandril_gray")

# 同じ画像ですが、異なる強度分布を持っています
img1 = adjust_histogram(img, GammaCorrection(gamma = 2))
img2 = adjust_histogram(img, GammaCorrection(gamma = 1.2))

# ミッドウェイヒストグラム均等化は、これら2つの画像を変換して
# それらの強度分布がほぼ同一になるようにします。
img_sequence = adjust_histogram([img1, img2], MidwayEqualization(nbins = 256))
img1o = first(img_sequence)
img2o = last(img_sequence)
```

# 参考文献

1. T. Guillemot and J. Delon, “*Implementation of the Midway Image Equalization*,” Image Processing On Line, vol. 5, pp. 114–129, Jun. 2016. [doi:10.5201/ipol.2016.140](https://doi.org/10.5201/ipol.2016.140)

```
