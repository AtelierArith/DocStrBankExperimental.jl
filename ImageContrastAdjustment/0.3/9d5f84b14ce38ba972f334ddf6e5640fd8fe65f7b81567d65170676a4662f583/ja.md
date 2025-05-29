```
edges, count = build_histogram(img)            # 8ビット画像のみ
edges, count = build_histogram(img, nbins)
edges, count = build_histogram(img, nbins; minval, maxval)
edges, count = build_histogram(img, edges)
```

画像のヒストグラムを`nbins`の間で`[minval, maxval]`に分けて生成します。カラー画像は自動的にグレースケールに変換されます。

# 出力

`edges`を返します。これは`AbstractRange`型で、区間`[minval, maxval]`がビンにどのように分割されるかを指定し、対応するビンの頻度を記録する配列`count`を返します。特に、`count`は以下の特性を持ちます：

  * `count[0]`は`x < edges[1]`を満たす数です。
  * `count[i]`は`edges[i] <= x < edges[i+1]`を満たす値`x`の数です。
  * `count[end]`は`x >= edges[end]`を満たす数です。
  * `length(count) == length(edges)+1`です。

# 詳細

ヒストグラムは確率密度関数$f$の区分定数モデルと考えることができます[1]。$f$がある区間$I = [a,b]$でサポートされていると仮定します。$m$を整数とし、$a = a_1 < a_2 < \ldots < a_m < a_{m+1} = b$を実数の列とします。区間の列を構築します。

$$
I_1 = [a_1,a_2], I_2 = (a_2, a_3], \ldots, I_{m} = (a_m,a_{m+1}]
$$

これは$I$を$f$が定数である部分集合$I_j$ $(j = 1, \ldots, m)$に分割します。これらの部分集合は$I_i \cap I_j = \emptyset, \forall i \neq j$を満たし、一般に*ビン*と呼ばれます。これらはデータ値の全範囲を包含し、$\sum_j |I_j | = | I |$が成り立ちます。各ビンの幅は$w_j = |I_j| = a_{j+1} - a_j$であり、高さ$h_j$はビンの領域における定数確率密度です。ビンの幅$w_j$にわたって定数確率密度を積分すると、ビンの確率質量$\pi_j = h_j w_j$が得られます。

サンプル$x_1, x_2, \ldots, x_N$について、

$$
n_j = \sum_{n = 1}^{N}\mathbf{1}_{(I_j)}(x_n),
\quad \text{where} \quad
\mathbf{1}_{(I_j)}(x) =
\begin{cases}
 1 & \text{if} \; x \in I_j,\\
 0 & \text{otherwise},
\end{cases},
$$

は区間$I_j$に落ちるサンプルの数を表します。$j$番目のビンの確率質量の推定値は相対頻度$\hat{\pi} = \frac{n_j}{N}$で与えられ、確率密度関数のヒストグラム推定器は次のように定義されます。

$$
\begin{aligned}
\hat{f}_n(x)  & = \sum_{j = 1}^{m}\frac{n_j}{Nw_j} \mathbf{1}_{(I_j)}(x) \\
& = \sum_{j = 1}^{m}\frac{\hat{\pi}_j}{w_j} \mathbf{1}_{(I_j)}(x) \\
& = \sum_{j = 1}^{m}\hat{h}_j \mathbf{1}_{(I_j)}(x).
\end{aligned}
$$

関数$\hat{f}_n(x)$は真の密度推定器です。なぜなら$\hat{f}_n(x)  \ge 0$であり、

$$
\begin{aligned}
\int_{-\infty}^{\infty}\hat{f}_n(x) \operatorname{d}x & = \sum_{j=1}^{m} \frac{n_j}{Nw_j} w_j \\
& = 1.
\end{aligned}
$$

# オプション

この関数のパラメータに関するさまざまなオプションが以下に詳述されています。

## `nbins`の選択肢

ヒストグラムの離散ビンの数を指定できます。ビンの数を指定する際は、画像タイプがサポートする最大のグレーレベル数を考慮してください。たとえば、`N0f8`タイプの画像では、最大256のグレーレベルがあります。したがって、そのタイプの画像に対して256を超えるビンを要求すると、多くのビンでゼロカウントが得られることを期待する必要があります。

## `minval`の選択肢

ヒストグラムが計算される区間の下限を指定するオプションがあります。`minval`が指定されていない場合、画像に存在する最小値が下限として取られます。

## `maxval`の選択肢

ヒストグラムが計算される区間の上限を指定するオプションがあります。`maxval`が指定されていない場合、画像に存在する最大値が上限として取られます。

## `edges`の選択肢

ビンの数、または区間の下限または上限を指定しない場合、`AbstractRange`型を指定することで区間がどのように分割されるかを直接指定するオプションがあります。

# 例

グレースケール画像のヒストグラムを計算します。

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray");
edges, counts  = build_histogram(img, 256, minval = 0, maxval = 1)
```

カラー画像が与えられた場合、赤チャネルのヒストグラムを計算します。

```julia
img = testimage("mandrill")
r = red.(img)
edges, counts  = build_histogram(r, 256, minval = 0, maxval = 1)
```

# 参考文献

[1] E. Herrholz, "Parsimonious Histograms," Ph.D. dissertation, Inst. of Math. and Comp. Sci., University of Greifswald, Greifswald, Germany, 2011. ```
