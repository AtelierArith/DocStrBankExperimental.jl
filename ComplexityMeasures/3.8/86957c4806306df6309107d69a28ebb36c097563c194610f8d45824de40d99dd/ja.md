```
SampleEntropy([x]; r = 0.2std(x), kwargs...) <: ComplexityEstimator
```

サンプルエントロピー複雑性測定の推定器 [Richman2000](@cite) で、[`complexity`](@ref) および [`complexity_normalized`](@ref) と共に使用されます。

入力時系列 `x` が提供されていない場合、キーワード引数 `r` は必須です。

## キーワード引数

  * `r::Real`: 点の周りの最近傍を照会する際に使用される半径。その値は、データの標準偏差のいくつかの割合として、入力データから決定されるべきです。
  * `m::Int = 2`: 埋め込み次元。
  * `τ::Int = 1`: 埋め込みラグ。

## 説明

半径 `r`、埋め込み次元 `m`、および埋め込みラグ `τ` を使用したサンプルエントロピーの*推定器*は次のようになります。

$$
SampEn(m,r, N) = -\ln{\dfrac{A(r, N)}{B(r, N)}}.
$$

ここで、

$$
\begin{aligned}
B(r, m, N) = \sum_{i = 1}^{N-m\tau} \sum_{j = 1, j \neq i}^{N-m\tau} \theta(d({\bf x}_i^m, {\bf x}_j^m) \leq r) \\
A(r, m, N) = \sum_{i = 1}^{N-m\tau} \sum_{j = 1, j \neq i}^{N-m\tau} \theta(d({\bf x}_i^{m+1}, {\bf x}_j^{m+1}) \leq r) \\
\end{aligned},
$$

ここで、$\theta(\cdot)$ は引数が真であれば 1 を返し、そうでなければ 0 を返し、$d(x, y)$ は $x$ と $y$ の間のチェビシェフ距離を計算し、${\bf x}_i^{m}$ と ${\bf x}_i^{m+1}$ は `m` 次元および `m+1` 次元の埋め込みベクトルであり、`k` 次元の埋め込みベクトルは入力時系列 $x(t)$ から次のように構築されます。

$$
{\bf x}_i^k = (x(i), x(i+τ), x(i+2τ), \ldots, x(i+(k-1)τ)).
$$

Richman & Moorman (2002) の引用: "SampEn(m,r,N) は B = 0 の場合を除いて定義され、これは規則性が検出されていないことを意味します。また、A = 0 の場合は条件付き確率が 0 であり、SampEn(m,r,N) の値が無限大になります。" これらの場合、`NaN` が返されます。

正規化された測定を計算する場合、結果のサンプルエントロピーは `[0, 1]` の範囲になります。

!!! note "柔軟な埋め込みラグ"
    元のアルゴリズムは `τ = 1` に固定されています。ここでのすべての式は、任意の `τ` に対応するように修正されています。


参照: [`entropy_sample`](@ref).
