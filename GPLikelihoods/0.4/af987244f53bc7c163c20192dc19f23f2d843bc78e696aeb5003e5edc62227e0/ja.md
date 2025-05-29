```
expected_loglikelihood(
    quadrature,
    lik,
    q_f::AbstractVector{<:Normal},
    y::AbstractVector,
)
```

この関数は期待対数尤度を計算します：

$$
    ∫ q(f) log p(y | f) df
$$

ここで `p(y | f)` はプロセス尤度です。これは `lik` によって記述され、`f` を入力として受け取り、`loglikelihood(lik(f), y)` をサポートする `y` に対する分布を返す呼び出し可能なものである必要があります。

`q(f)` は潜在関数値 `f` の近似であり、次のように与えられます：

$$
    q(f) = ∫ p(f | u) q(u) du
$$

ここで `q(u)` は誘導点に対する変分分布です。`q(f)` の周辺分布は `q_f` によって与えられます。

`quadrature` は期待対数尤度を計算するために使用される方法を決定します。

# 拡張ヘルプ

`q(f)` は `MvNormal` 分布であると仮定され、`p(y | f)` は独立した周辺を持つと仮定されており、`q(f)` の周辺のみが必要です。
