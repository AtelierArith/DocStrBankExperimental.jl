```
truncated(d0::UnivariateDistribution; [lower::Real], [upper::Real])
truncated(d0::UnivariateDistribution, lower::Real, upper::Real)
```

分布 `d0` を区間 $[l, u]=$`[lower, upper]` に切り取った *切り取られた分布* `d` は、確率密度（質量）関数を持ちます：

$$
f(x; d_0, l, u) = \frac{f_{d_0}(x)}{P_{Z \sim d_0}(l \le Z \le u)}, \quad x \in [l, u],
$$

ここで $f_{d_0}(x)$ は $d_0$ の確率密度（質量）関数です。

$$
l > u
$$

の場合、関数はエラーをスローします。

```julia
truncated(d0; lower=l)           # d0 は区間 [l, Inf) に左切り取られます
truncated(d0; upper=u)           # d0 は区間 (-Inf, u] に右切り取られます
truncated(d0; lower=l, upper=u)  # d0 は区間 [l, u] に切り取られます
truncated(d0, l, u)              # d0 は区間 [l, u] に切り取られます
```

関数は [`Truncated`](@ref) ラッパーの構築にフォールバックします。

# 実装

タイプ `D` の分布に対して特化した切り取られた形式を実装するには、以下のメソッドの1つ以上を実装する必要があります：

  * `truncated(d0::D, l::T, u::T) where {T <: Real}`: 区間切り取り
  * `truncated(d0::D, ::Nothing, u::Real)`: 右切り取り
  * `truncated(d0::D, l::Real, u::Nothing)`: 左切り取り

```
