```
LagrangianHessian{CO, V, T}
```

変数 $p$ に関する [`ConstrainedManifoldObjective`](@ref) `co` のラグランジアンのヘッセ行列。式は次のように表されます。

$$
\operatorname{Hess}_p \mathcal L(p; μ, λ)[X]
= \operatorname{Hess} f(p) +  \sum_{i=1}^m μ_i \operatorname{Hess} g_i(p)[X] + \sum_{j=1}^n λ_j \operatorname{Hess} h_j(p)[X]
$$

# フィールド

  * `co::CO`, `μ::T`, `λ::T` は前述の通りで、`T` はベクトル型を表します。

# コンストラクタ

```
LagrangianHessian(co, μ, λ)
```

固定された双対変数を持つラグランジアンのファンクタを作成します。

# 例

ラグランジアンのヘッセ行列 $\operatorname{Hess}_p \mathcal L$ を直接評価したい場合は、`LagrangianHessian(co, μ, λ)(M, p, X)` またはインプレースバリアントのために `LagrangianHessian(co, μ, λ)(M, Y, p, X)` を呼び出すこともできます。
