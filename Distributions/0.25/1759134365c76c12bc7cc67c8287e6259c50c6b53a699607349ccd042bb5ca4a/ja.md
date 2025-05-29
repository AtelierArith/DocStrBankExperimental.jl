```
censored(d0::UnivariateDistribution; [lower::Real], [upper::Real])
censored(d0::UnivariateDistribution, lower::Real, upper::Real)
```

分布 `d0` の *検閲分布* `d` は区間 $[l, u]=$`[lower, upper]` に対して、確率密度（質量）関数を持ちます：

$$
f(x; d_0, l, u) = \begin{cases}
    P_{Z \sim d_0}(Z \le l), & x = l \\
    f_{d_0}(x),              & l < x < u \\
    P_{Z \sim d_0}(Z \ge u), & x = u \\
  \end{cases}, \quad x \in [l, u]
$$

ここで、$f_{d_0}(x)$ は $d_0$ の確率密度（質量）関数です。

もし $Z \sim d_0$ であり、`X = clamp(Z, l, u)` であれば、$X \sim d$ となります。これは、$d_0$ が連続であっても、その検閲形式が境界 $l$ と $u$ に正の確率を割り当てることを意味します。したがって、検閲された連続分布は原子を持ち、離散成分と連続成分の混合物です。

この関数は [`Distributions.Censored`](@ref) ラッパーの構築に戻ります。

# 使用法

```julia
censored(d0; lower=l)           # d0 を区間 [l, Inf) に左検閲
censored(d0; upper=u)           # d0 を区間 (-Inf, u] に右検閲
censored(d0; lower=l, upper=u)  # d0 を区間 [l, u] に区間検閲
censored(d0, l, u)              # d0 を区間 [l, u] に区間検閲
```

# 実装

型 `D` の分布に対して特化した検閲形式を実装するには、上記のシグネチャのいずれかでメソッドをオーバーロードするのではなく、以下のメソッドの1つ以上を実装する必要があります：

  * `censored(d0::D, l::T, u::T) where {T <: Real}`
  * `censored(d0::D, ::Nothing, u::Real)`
  * `censored(d0::D, l::Real, ::Nothing)`

```
