```
    Equalization <: AbstractHistogramAdjustmentAlgorithm
    Equalization(; nbins = 256, minval = 0, maxval = 1)

    adjust_histogram([T,] img, f::Equalization)
    adjust_histogram!([out,] img, f::Equalization)
```

`nbins`のビン数でヒストグラム均等化された画像を返します。

# 詳細

ヒストグラム均等化は、単一チャネルのグレースケール画像のコントラストを改善するために最初に考案されました。この手法は、画像内の強度の分布をできるだけ均一に変換します[1]。均一性の自然な正当化は、画像の強度レベルが強度スケール上で広範囲にわたる場合、画像のコントラストが良くなるということです。必要な変換は、累積ヒストグラムに基づくマッピングであることがわかります。

$$
L
$$

ビットの単一チャネル$I \times J$画像を、グレー値が集合$\{0,1,\ldots,L-1 \}$にある独立かつ同一分布の確率変数のコレクションと考えることができます。具体的には、サンプル空間$\Omega$をすべての$IJ$-タプル$\omega =(\omega_{11},\omega_{12},\ldots,\omega_{1J},\omega_{21},\omega_{22},\ldots,\omega_{2J},\omega_{I1},\omega_{I2},\ldots,\omega_{IJ})$の集合とし、各$\omega_{ij} \in \{0,1,\ldots, L-1 \}$とします。さらに、関数$\Omega \ni \omega \to \omega_{ij} \in \{0,1,\ldots,L-1\}$が独立かつ同一分布であるように、$\Omega$に確率測度を課します。

次に、画像を確率変数の行列$\mathbf{G} = [G_{i,j}(\omega)]$として考えることができ、各関数$G_{i,j}: \Omega \to \mathbb{R}$は次のように定義されます。

$$
G_{i,j}(\omega) = \frac{\omega_{ij}}{L-1},
$$

そして各$G_{i,j}$は未知の密度$f_{G}$に従って分布します。$f_{G}$は未知ですが、グレー値の正規化ヒストグラムで近似することができます。

$$
\hat{f}_{G}(v)= \frac{n_v}{IJ},
$$

ここで

$$
n_v = \left | \left\{(i,j)\, |\,  G_{i,j}(\omega)  = v \right \} \right |
$$

は、強度$v$のグレー レベルが$\mathbf{G}$に出現する回数を表します。強度の分布をできるだけ均一に変換するには、$T(\cdot)$というマッピングを見つける必要があります。$T(G_{i,j}) \thicksim U$となるように。必要なマッピングは、経験的密度$\hat{f}_{G}$の累積分布関数（CDF）であることがわかります。

$$
 T(G_{i,j}) = \int_0^{G_{i,j}}\hat{f}_{G}(w)\mathrm{d} w.
$$

# オプション

`adjust_histogram`関数および`Equalization`型のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img`の選択肢

`adjust_histogram`関数は、さまざまな入力タイプを処理できます。デフォルトでは、返される画像の型は入力型と一致します。

カラー画像の場合、入力は[YIQ](https://en.wikipedia.org/wiki/YIQ)型に変換され、Yチャネルが均等化されます。これはIおよびQチャネルと組み合わされ、結果の画像は入力と同じ型に変換されます。

## `Equalization`における`nbins`の選択肢

ヒストグラムのビンの総数を指定できます。

## `Equalization`における`minval`および`maxval`の選択肢

`minval`および`maxval`が指定されている場合、強度は範囲[`minval`, `maxval`]に均等化されます。デフォルト値は0と1です。

# 例

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray")
imgeq = adjust_histogram(img, Equalization(nbins = 256, minval = 0, maxval = 1))

imshow(img)
imshow(imgeq)
```

# 参考文献

1. R. C. Gonzalez and R. E. Woods. *Digital Image Processing (3rd Edition)*.  Upper Saddle River, NJ, USA: Prentice-Hall,  2006.

```
