```
fixedmass_correlationsum(X [, max_j]; metric = Euclidean(), M = length(X)) → rs, ys
```

[`correlationsum`](@ref) の計算のための固定質量アルゴリズムであり、その後、`max_j` は計算に考慮すべき最大の隣接点の数です。

デフォルトでは `max_j = clamp(N*(N-1)/2, 5, 32)` で、`N` はデータの長さです。

## キーワード引数

  * `M` は、`X` からランダムにサンプリングされた距離の平均化に考慮される点の数を定義します。
  * `metric = Euclidean()` は距離のメトリックです。
  * `start_j = 4` は、`j = start_j` から始めて以下の方程式を計算します。通常、最初の `j` 値はフラクタル次元の正しいスケーリングに収束していません。

## 説明

「固定質量」アルゴリズムは、半径内のすべての隣接点を見つけようとするのではなく、代わりに `j` 点を含む最大半径を見つけようとします。この制約により相関和が得られ、同様に `k` 点を含む平均半径が得られます。これに基づいて、情報次元を近似する $\Delta$ を計算できます。ここでの実装は [Grassberger1988](@cite) に基づいており、次のように定義されています。

$$
Ψ(j) - \log N \sim \Delta \times \overline{\log \left( r_{(j)}\right)}
$$

ここで、$\Psi(j) = \frac{\text{d} \log Γ(j)}{\text{d} j}$ はディガンマ関数、`rs` = $\overline{\log \left( r_{(j)}\right)}$ は `j` 隣接点を含む半径の平均対数、`ys` = $\Psi(j) - \log N$ （$N$ はデータの長さ）です。見つかった隣接点の数 $j$ は 2 から `max_j` までの範囲です。数値はまた、基数 $e$ から基数 $2$ に変換されます。

$$
\Delta
$$

は `linear_region(rs, ys)` を使用して計算できます。
