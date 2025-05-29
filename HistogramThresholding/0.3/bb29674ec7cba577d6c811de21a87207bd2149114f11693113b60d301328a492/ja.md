```
find_threshold(counts, edges, Entropy())
t = find_threshold(img, Entropy(); nbins = 256)
```

ヒストグラムのエントロピーを使用して、グレーレベルヒストグラムのしきい値を見つけるためのアルゴリズムです。

# 出力

ヒストグラムのしきい値ビンに対応する `AbstractRange` のポイントを返します。

# 拡張ヘルプ

# 詳細

このアルゴリズムは、グレーレベルヒストグラムのエントロピーを使用してしきい値を生成します。

$$
f_1, f_2, \ldots, f_I
$$

をヒストグラムのさまざまなビンの頻度とし、$I$ をビンの数とします。$N = \sum_{i=1}^{I}f_i$ とし、$p_i = \frac{f_i}{N}$ ($i = 1, \ldots, I$) をグレーレベルの確率分布とします。この分布から、2つの追加の分布を導出します。最初は離散値 $1$ から $s$ まで、もう一つは $s+1$ から $I$ までのものです。これらの分布は次のようになります。

$$
A: \frac{p_1}{P_s}, \frac{p_2}{P_s}, \ldots, \frac{p_s}{P_s}
\quad \text{および} \quad
B: \frac{p_{s+1}}{1-P_s}, \ldots, \frac{p_n}{1-P_s}
\quad \text{ここで} \quad
P_s = \sum_{i=1}^{s}p_i.
$$

各分布に関連するエントロピーは次のようになります。

$$
H(A) = \ln(P_s) + \frac{H_s}{P_s}
$$

$$
H(B) = \ln(1-P_s) + \frac{H_n-H_s}{1-P_s}
$$

$$
\quad \text{ここで} \quad
H_s = -\sum_{i=1}^{s}p_i\ln{p_i}
\quad \text{および} \quad
H_n = -\sum_{i=1}^{I}p_i\ln{p_i}.
$$

これら2つのエントロピー関数を組み合わせると、次のようになります。

$$
\psi(s) = \ln(P_s(1-P_s)) + \frac{H_s}{P_s} + \frac{H_n-H_s}{1-P_s}.
$$

関数 $\psi(s)$ を最大化する離散値 $s$ を見つけることで、求めるしきい値（すなわちしきい値を決定するビン）が得られます。

エントロピーの導出に関する詳細は、[1]のセクション4を参照してください。

# オプション

## `counts` の選択肢

ヒストグラムの頻度の1D配列である `AbstractArray` を指定できます。ヒストグラムのビンに対応する `edges` 範囲を提出する必要があります。`edges` と `counts` の長さが異なる場合、関数はエラーをスローします。

## `edges` の選択肢

`counts` に渡されたヒストグラム配列のビンに対応する範囲である `AbstractRange` を指定できます。

# 例

```julia

using TestImages, Images

img = testimage("cameraman")
# 256ビンのヒストグラムを構築
edges, counts = build_histogram(img, 256)
#=
  `counts` 配列は、インデックス0に最初のビンエッジよりも低い頻度を格納します。
  `edges` によって区切られた区間でしきい値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  そうすることで、`edges` と `counts` の次元が一致します。
=#
find_threshold(counts[1:end], edges, Entropy())
```

# 参考文献

[1] J. N. Kapur, P. K. Sahoo, and A. K. C. Wong, “A new method for gray-level picture thresholding using the entropy of the histogram,” *Computer Vision, Graphics, and Image Processing*, vol. 29, no. 1, p. 140, Jan. 1985.[doi:10.1016/s0734-189x(85)90156-2](https://doi.org/10.1016/s0734-189x%2885%2990156-2)
