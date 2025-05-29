```
ProximalDCGrad
```

関数 `(M,X,p) → ℝ` は、[`ManifoldDifferenceOfConvexProximalObjective`](@ref) の内部コスト関数の勾配を表します。これは `g` の近接マップコスト関数の勾配関数です。次に基づいています。

$$
    F_{p_k}(p) = \frac{1}{2λ}d_{\mathcal M}(p_k,p)^2 + g(p)
$$

これは次のように読み取れます。

$$
    \operatorname{grad} F_{p_k}(p) = \operatorname{grad} g(p) - \frac{1}{λ}\log_p p_k
$$

点 `pk` と近接パラメータ `λ` に対して。

# フィールド

  * `grad_g`  - 勾配関数
  * `pk` - マンフォールド上の点
  * `λ`  - 近接パラメータ

両方の中間値は、`set_parameter!(::ProximalDCGrad, ::Val{:p}, p)` および `set_parameter!(::ProximalDCGrad, ::Val{:λ}, λ)` を使用して設定できます。

# コンストラクタ

```
ProximalDCGrad(grad_g, pk, λ; evaluation=AllocatingEvaluation())
```

ここでは、`grad_g` が [`AllocatingEvaluation`](@ref) または [`InplaceEvaluation`](@ref) であるかを指定しますが、この関数は常に *両方* のシグネチャを提供します。
