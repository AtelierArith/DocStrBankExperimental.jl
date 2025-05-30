```
t = find_threshold(histogram, edges, Moments())
t = find_threshold(img, Moments(); nbins = 256)
```

以下のルールが閾値を決定します：閾値未満のすべての観測値に値 z₀ を割り当て、閾値以上のすべての観測値に値 z₁ を割り当てると、元のヒストグラムの最初の3つのモーメントは、この特別に構築された二値ヒストグラムのモーメントと一致しなければなりません。

# 出力

実数 `t` を `edges` で返します。`edges` パラメータは、ヒストグラムビンに関連付けられた区間を指定する `AbstractRange` を表します。

# 拡張ヘルプ

# 詳細

$$
f_i
$$

$(i=1 \ldots I)$ をヒストグラムの $i$ 番目のビンにおける観測値の数、$z_i$ $(i=1 \ldots I)$ を $i$ 番目のビンに関連付けられた観測値とします。 すると、観測値 $z_i$ が $i$ 番目のビンに属する確率は $p_i = \frac{f_i}{N}$ ($i = 1, \ldots, I$) で与えられ、ここで $N = \sum_{i=1}^{I}f_i$ です。

モーメントは、次のようにヒストグラム $f$ から計算できます：

$$
m_k = \frac{1}{N} \sum_i p_i (z_i)^k \quad k = 0,1,2,3, \ldots.
$$

モーメント保存閾値の原則は、閾値を選択し、2つの代表値 $z_0$ と $z_1$ ($z_0 < z_1$) を選ぶことです。これにより、$f$ の閾値未満のすべての値が $z_0$ に置き換えられ、閾値以上のすべての値が $z_1$ に置き換えられると、この特別に構築された二値ヒストグラム $g$ は $f$ と同じ最初の3つのモーメントを持つことになります。

具体的には、$q_0$ と $q_1$ を $f$ における閾値未満および閾値以上の観測値の割合とします。$g$ の最初の3つのモーメントが $f$ の最初の3つのモーメントと等しいという制約は、次の4つの方程式の系で表現できます。

$$
\begin{aligned}
   q_0 (z_0)^0 + q_1 (z_1)^0   & = m_0 \\
   q_0 (z_0)^1 + q_1 (z_1)^1   & = m_1 \\
   q_0 (z_0)^2 + q_1 (z_1)^2   & = m_2 \\
   q_0 (z_0)^3 + q_1 (z_1)^3   & = m_3 \\
\end{aligned}
$$

ここで、左辺は $g$ のモーメントを表し、右辺は $f$ のモーメントを表します。望ましい閾値を見つけるためには、まず4つの方程式を解いて $q_0$ と $q_1$ を得てから、$q_0 = \sum_{z_i \le t} p_i$ となるように閾値 $t$ を選びます。

# 引数

関数の引数は以下でより詳細に説明されています。

## `histogram`

頻度分布を格納する `AbstractArray`。

## `edges`

頻度分布の区間がどのように分割されるかを指定する `AbstractRange`。

# 例

`TestImages` パッケージの「カメラマン」画像の閾値を計算します。

```julia
using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("cameraman")
edges, counts = build_histogram(img,256)
#=
  `counts` 配列は、インデックス 0 に最初のビンのエッジ未満の頻度を格納します。
  `edges` によって区切られた区間に対して閾値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  そうすることで、`edges` と `counts` の次元が一致します。
=#
t = find_threshold(counts[1:end], edges, Moments())
```

# 参考文献

[1] W.-H. Tsai, “Moment-preserving thresolding: A new approach,” Computer Vision, Graphics, and Image Processing, vol. 29, no. 3, pp. 377–393, Mar. 1985. [doi:10.1016/0734-189x(85)90133-1](https://doi.org/10.1016/0734-189x%2885%2990133-1)
