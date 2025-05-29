```
hist_equalised_img = histeq(img, nbins)
hist_equalised_img = histeq(img, nbins, minval, maxval)
```

約 `nbins` 個のビンの粒度を持つヒストグラム均等化画像を返します。

# 詳細

ヒストグラム均等化は、最初に単一チャネルのグレースケール画像のコントラストを改善するために考案されました。この手法は、画像内の強度の分布をできるだけ均一に変換します [1]。均一性の自然な正当化は、画像の強度レベルが強度スケール上で広範囲にわたる場合、画像のコントラストが良くなるということです。必要な変換は、累積ヒストグラムに基づくマッピングであることがわかります。

$$
L
$$

ビットの単一チャネル $I \times J$ 画像を、グレー値が $\{0,1,\ldots,L-1 \}$ の集合である独立かつ同一分布の確率変数のコレクションと考えることができます。具体的には、サンプル空間 $\Omega$ をすべての $IJ$-タプル $\omega =(\omega_{11},\omega_{12},\ldots,\omega_{1J},\omega_{21},\omega_{22},\ldots,\omega_{2J},\omega_{I1},\omega_{I2},\ldots,\omega_{IJ})$ の集合とし、各 $\omega_{ij} \in \{0,1,\ldots, L-1 \}$ であるとします。さらに、関数 $\Omega \ni \omega \to \omega_{ij} \in \{0,1,\ldots,L-1\}$ が独立かつ同一分布であるように、$\Omega$ に確率測度を課します。

次に、画像を確率変数の行列 $\mathbf{G} = [G_{i,j}(\omega)]$ と見なすことができ、各関数 $G_{i,j}: \Omega \to \mathbb{R}$ は次のように定義されます。

$$
G_{i,j}(\omega) = \frac{\omega_{ij}}{L-1},
$$

そして各 $G_{i,j}$ は未知の密度 $f_{G}$ に従って分布します。$f_{G}$ は未知ですが、グレーレベルの正規化されたヒストグラムで近似することができます。

$$
\hat{f}_{G}(v)= \frac{n_v}{IJ},
$$

ここで

$$
n_v = \left | \left\{(i,j)\, |\,  G_{i,j}(\omega)  = v \right \} \right |
$$

は、強度 $v$ のグレーレベルが $\mathbf{G}$ に出現する回数を表します。強度の分布をできるだけ均一に変換するためには、$T(\cdot)$ というマッピングを見つける必要があります。$T(G_{i,j}) \thicksim U$ となるようにします。必要なマッピングは、経験的密度 $\hat{f}_{G}$ の累積分布関数 (CDF) であることがわかります。

$$
 T(G_{i,j}) = \int_0^{G_{i,j}}\hat{f}_{G}(w)\mathrm{d} w.
$$

# オプション

この関数のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img` の選択肢

`histeq` 関数はさまざまな入力タイプを処理できます。返される画像は入力タイプに依存します。入力が `Image` の場合、結果の画像は同じタイプであり、同じ特性を持ちます。

カラー画像の場合、入力は [YIQ](https://en.wikipedia.org/wiki/YIQ) タイプに変換され、Y チャンネルが均等化されます。これは I および Q チャンネルと組み合わされ、結果の画像は入力と同じタイプに変換されます。

## `nbins` の選択肢

ヒストグラムのビンの総数を指定できます。

## `minval` と `maxval` の選択肢

minval と maxval が指定されている場合、強度は範囲 (minval, maxval) に均等化されます。デフォルト値は 0 と 1 です。

# 例

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray");
imgeq = histeq(img,256);

imshow(img)
imshow(imgeq)
```

# 参考文献

1. R. C. Gonzalez and R. E. Woods. *Digital Image Processing (3rd Edition)*.  Upper Saddle River, NJ, USA: Prentice-Hall,  2006.

参照も: [histmatch](@ref),[clahe](@ref), [imhist](@ref) および  [adjust_gamma](@ref). ```
