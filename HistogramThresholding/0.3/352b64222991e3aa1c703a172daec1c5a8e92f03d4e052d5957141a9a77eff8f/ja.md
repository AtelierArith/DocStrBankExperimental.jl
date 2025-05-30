```
t = find_threshold(histogram, edges, MinimumError())
t = find_threshold(img, MinimumError(); nbins = 256)
```

ヒストグラムが二つのガウス分布の混合であると仮定した場合、しきい値は期待される誤分類エラー率が最小化されるように選択されます。

# 出力

実数 `t` を `edges` で返します。`edges` パラメータは、ヒストグラムビンに関連する区間を指定する `AbstractRange` を表します。

# 拡張ヘルプ

# 詳細

$$
f_i
$$

$(i=1 \ldots I)$ をヒストグラムの $i$ 番目のビンにおける観測数とします。すると、観測が $i$ 番目のビンに属する確率は $p_i = \frac{f_i}{N}$ ($i = 1, \ldots, I$) で与えられ、ここで $N = \sum_{i=1}^{I}f_i$ です。

最小エラーしきい値法は、データを二つのカテゴリ $C_0$ と $C_1$ に分割するしきい値 $T$ を見つけることができると仮定し、データは二つのガウス分布の混合としてモデル化できるとします。次のように定義します。

$$
P_0(T) = \sum_{i = 1}^T p_i \quad \text{and} \quad P_1(T) = \sum_{i = T+1}^I p_i
$$

累積確率を表し、

$$
\mu_0(T) = \sum_{i = 1}^T i \frac{p_i}{P_0(T)} \quad \text{and} \quad \mu_1(T) = \sum_{i = T+1}^I i \frac{p_i}{P_1(T)}
$$

平均を表し、

$$
\sigma_0^2(T) = \sum_{i = 1}^T (i-\mu_0(T))^2 \frac{p_i}{P_0(T)} \quad \text{and} \quad \sigma_1^2(T) = \sum_{i = T+1}^I (i-\mu_1(T))^2 \frac{p_i}{P_1(T)}
$$

カテゴリ $C_0$ と $C_1$ の分散を表します。

キトラーとイリングワースは、次の最小エラー基準関数を使用することを提案しました。

$$
J(T) = 1 + 2 \left[ P_0(T) \ln \sigma_0(T) + P_1(T) \ln \sigma_1(T) \right] - 2 \left[P_0(T) \ln P_0(T) + P_1(T) \ln P_1(T) \right]
$$

これは、特定のしきい値 $T$ によって示されるガウスの混合と、ヒストグラムによって表される区分定数確率密度関数との不一致を評価します。関数 $J(T)$ を最小化する離散値 $T$ が求めるしきい値（すなわち、しきい値を決定するビン）を生成します。

# 引数

関数の引数は以下でより詳細に説明されています。

## `histogram`

頻度分布を格納する `AbstractArray`。

## `edges`

頻度分布の区間がどのように分割されるかを指定する `AbstractRange`。

# 例

`TestImages` パッケージの「カメラマン」画像のしきい値を計算します。

```julia
using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("cameraman")
edges, counts = build_histogram(img,256)
#=
  `counts` 配列は、インデックス 0 に最初のビンのエッジよりも低い頻度を格納します。
  `edges` によって区切られた区間に対してしきい値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  これにより、`edges` と `counts` の次元が一致します。
=#
t = find_threshold(counts[1:end], edges, MinimumError())
```

# 参考文献

1. J. Kittler and J. Illingworth, “Minimum error thresholding,” Pattern Recognition, vol. 19, no. 1, pp. 41–47, Jan. 1986. [doi:10.1016/0031-3203(86)90030-0](https://doi.org/10.1016/0031-3203%2886%2990030-0)
2. Q.-Z. Ye and P.-E. Danielsson, “On minimum error thresholding and its implementations,” Pattern Recognition Letters, vol. 7, no. 4, pp. 201–206, Apr. 1988. [doi:10.1016/0167-8655(88)90103-1](https://doi.org/10.1016/0167-8655%2888%2990103-1)
