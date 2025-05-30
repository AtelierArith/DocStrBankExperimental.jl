```
t = find_threshold(histogram, edges, Otsu())
t = find_threshold(img, Otsu(); nbins = 256)
```

ヒストグラムが二峰性であると仮定した場合、しきい値は結果として得られるクラス間分散が最大になるように設定されます。

# 出力

実数 `t` を `edges` で返します。`edges` パラメータは、ヒストグラムビンに関連する区間を指定する `AbstractRange` を表します。

# 拡張ヘルプ

# 詳細

$$
f_i
$$

$(i=1 \ldots I)$ をヒストグラムの $i$ 番目のビンにおける観測数とします。すると、観測が $i$ 番目のビンに属する確率は $p_i = \frac{f_i}{N}$ ($i = 1, \ldots, I$) で与えられ、ここで $N = \sum_{i=1}^{I}f_i$ です。

しきい値 $T$ の選択はデータを二つのカテゴリ $C_0$ と $C_1$ に分割します。次のように定義します。

$$
P_0(T) = \sum_{i = 1}^T p_i \quad \text{および} \quad P_1(T) = \sum_{i = T+1}^I p_i
$$

累積確率を表し、

$$
\mu_0(T) = \sum_{i = 1}^T i \frac{p_i}{P_0(T)} \quad \text{および} \quad \mu_1(T) = \sum_{i = T+1}^I i \frac{p_i}{P_1(T)}
$$

平均を表し、

$$
\sigma_0^2(T) = \sum_{i = 1}^T (i-\mu_0(T))^2 \frac{p_i}{P_0(T)} \quad \text{および} \quad \sigma_1^2(T) = \sum_{i = T+1}^I (i-\mu_1(T))^2 \frac{p_i}{P_1(T)}
$$

カテゴリ $C_0$ と $C_1$ の分散を表します。さらに、

$$
\mu = P_0(T)\mu_0(T) + P_1(T)\mu_1(T),
$$

全体の平均を表し、

$$
\sigma_b^2(T) = P_0(T)(\mu_0(T) - \mu)^2 + P_1(T)(\mu_1(T) - \mu)^2,
$$

クラス間分散を表し、

$$
\sigma_w^2(T) = P_0(T) \sigma_0^2(T) +  P_1(T)\sigma_1^2(T)
$$

クラス内分散を表します。

関数 $\sigma_b^2(T)$ を最大化する離散値 $T$ を見つけることで、求めるしきい値（すなわちしきい値を決定するビン）を得ることができます。実際、そのしきい値はクラス内分散基準 $\sigma_w^2(T)$ を最小化することによって決定されるしきい値と等しくなります。さらに、そのしきい値はクラス間分散とクラス内分散の比を最大化することによって計算されたしきい値とも同じです。

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
  `counts` 配列はインデックス 0 において最初のビンのエッジよりも低い頻度を格納します。
  `edges` によって区切られた区間に対してしきい値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  そうすることで `edges` と `counts` の次元が一致します。
=#
t = find_threshold(counts[1:end], edges, Otsu())
```

# 参考文献

1. Nobuyuki Otsu (1979). “A threshold selection method from gray-level histograms”. *IEEE Trans. Sys., Man., Cyber.* 9 (1): 62–66. [doi:10.1109/TSMC.1979.4310076](http://dx.doi.org/doi:10.1109/TSMC.1979.4310076)

```
