```
ProximalDCCost
```

関手 `(M, p) → ℝ` は、[`ManifoldDifferenceOfConvexProximalObjective`](@ref) の内部コスト関数を表します。これは `g` の近接写像のコスト関数です。

$$
    F_{p_k}(p) = \frac{1}{2λ}d_{\mathcal M}(p_k,p)^2 + g(p)
$$

点 `pk` と近接パラメータ $λ$ に対して。

# フィールド

  * `g`  - 関数
  * `pk` - 多様体上の点
  * `λ`  - 近接パラメータ

両方の中間値は、`set_parameter!(::ProximalDCCost, ::Val{:p}, p)` と `set_parameter!(::ProximalDCCost, ::Val{:λ}, λ)` を使用してそれぞれ設定できます。

# コンストラクタ

```
ProximalDCCost(g, p, λ)
```
