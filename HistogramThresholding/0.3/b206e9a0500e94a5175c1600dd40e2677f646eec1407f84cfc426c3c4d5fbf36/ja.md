```
t = find_threshold(histogram, edges, Yen())
t = find_threshold(img, Yen(); nbins = 256)
```

Yenの最大相関基準を使用して二値しきい値を計算します。

# 出力

実数 `t` を `edges` で返します。`edges` パラメータは、ヒストグラムビンに関連する区間を指定する `AbstractRange` を表します。

# 拡張ヘルプ

# 詳細

このアルゴリズムは、しきい値を生成するためにグレーレベルヒストグラムの *エントロピー相関* の概念を使用します。

$$
f_1, f_2, \ldots, f_I
$$

をヒストグラムのさまざまなビンの頻度とし、$I$ をビンの数とします。$N = \sum_{i=1}^{I}f_i$ とし、$p_i = \frac{f_i}{N}$ ($i = 1, \ldots, I$) をグレーレベルの確率分布とします。この分布から、2つの追加の分布を導出します。最初は離散値 $1$ から $s$ まで、もう一つは $s+1$ から $I$ までです。これらの分布は次のようになります。

$$
A: \frac{p_1}{P_s}, \frac{p_2}{P_s}, \ldots, \frac{p_s}{P_s}
\quad \text{および} \quad
B: \frac{p_{s+1}}{1-P_s}, \ldots, \frac{p_n}{1-P_s}
\quad \text{ここで} \quad
P_s = \sum_{i=1}^{s}p_i.
$$

各分布に関連するエントロピー相関は次のようになります。

$$
C(A) = -\ln \sum_{i=1}^{s} \left( \frac{p_i}{P_s} \right)^2 \quad \text{および} \quad C(B) = -\ln \sum_{i=s+1}^{I} \left( \frac{p_i}{1 - P_s} \right)^2.
$$

これら2つのエントロピー相関関数を組み合わせると、次のようになります。

$$
\psi(s) = -\ln \sum_{i=1}^{s} \left( \frac{p_i}{P_s} \right)^2 -\ln \sum_{i=s+1}^{I} \left( \frac{p_i}{1 - P_s} \right)^2.
$$

関数 $\psi(s)$ を最大化する離散値 $s$ を見つけることで、求めるしきい値（すなわち、しきい値を決定するビン）が得られます。

# 引数

関数の引数は以下に詳述されています。

## `histogram`

頻度分布を格納する `AbstractArray`。

## `edges`

頻度分布の区間がどのように分割されるかを指定する `AbstractRange`。

# 例

`TestImages` パッケージの「カメラマン」画像のしきい値を計算します。

```julia

using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("cameraman")
edges, counts = build_histogram(img, 256)
#=
  `counts` 配列は、インデックス 0 に最初のビンのエッジよりも低い頻度を格納します。
  `edges` によって区切られた区間に対してしきい値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  そうすることで、`edges` と `counts` の次元が一致します。
=#
t = find_threshold(counts[1:end], edges, Yen())
```

# 参考文献

1. Yen JC, Chang FJ, Chang S (1995), “A New Criterion for Automatic Multilevel Thresholding”, IEEE Trans. on Image Processing 4 (3): 370-378, [doi:10.1109/83.366472](https://doi.org/10.1109/83.366472)

```
