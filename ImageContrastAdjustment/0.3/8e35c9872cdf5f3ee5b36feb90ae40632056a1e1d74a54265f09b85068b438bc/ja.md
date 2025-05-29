```
    GammaCorrection <: AbstractHistogramAdjustmentAlgorithm
    GammaCorrection(; gamma = 1)

    adjust_histogram([T,] img, f::GammaCorrection)
    adjust_histogram!([out,] img, f::GammaCorrection)
```

ガンマ補正された画像を返します。

# 詳細

ガンマ補正は、次の関係によって与えられる非線形変換です。

$$
f(x) = x^\gamma \quad \text{for} \; x \in \mathbb{R}, \gamma > 0.
$$

これは、ある量が別の量のべき乗として変化するため、*べき法則*変換と呼ばれます。

ガンマ補正は、物理デバイスによって生成される光の強度が通常は適用された信号の線形関数ではなく、代わりにべき法則に従うという事実を補償するために、画像を前処理するために歴史的に使用されてきました[1]。たとえば、多くの陰極線管（CRT）では、表示される光の強度は、γのべき乗に上げられた電圧にほぼ等しく、γ ∈ [1.8, 2.8]です。したがって、1/γの指数で生の画像を前処理することで、明るさに対する線形応答が保証されます。

心理物理学の研究でも、光の強度と知覚的明るさの間に[経験的なべき法則](https://en.wikipedia.org/wiki/Stevens%27s_power_law)が確立されています。したがって、ガンマ補正はしばしば有用な画像強調ツールとして機能します。

# オプション

`adjust_histogram`関数および`Gamma`型のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img`の選択肢

この関数はさまざまな入力タイプを処理できます。返される画像は入力タイプに依存します。

カラー画像の場合、入力はYIQタイプに変換され、Yチャネルがガンマ補正されます。これはIおよびQチャネルと組み合わされ、結果の画像は入力と同じタイプに変換されます。

## `gamma`の選択

`gamma`値はゼロでない正の数でなければなりません。1未満の`gamma`値は明るい画像を生成し、1より大きい値は暗い画像を生成します。指定しない場合は、デフォルト値として1が仮定されます。

# 例

```julia
using ImageContrastAdjustment, ImageView

# 強度の線形ランプからなる例の画像を作成します。
n = 32
intensities = 0.0:(1.0/n):1.0
img = repeat(intensities, inner=(20,20))'

# 暗いトーンを明るくします。
imgadj = adjust_histogram( img, GammaCorrection(gamma = 1/2))

# 元の画像と調整された画像を表示します。
imshow(img)
imshow(imgadj)
```

# 参考文献

1. W. Burger and M. J. Burge. *デジタル画像処理*. コンピュータサイエンスのテキスト, 2016. [doi:10.1007/978-1-4471-6684-9](https://doi.org/10.1007/978-1-4471-6684-9)
