```
LagrangianCost{CO,T} <: AbstractConstrainedFunctor{T}
```

[`ConstrainedManifoldObjective`](@ref) `co` のラグランジアンを実装します。

$$
\mathcal L(p; μ, λ)
= f(p) +  \sum_{i=1}^m μ_ig_i(p) + \sum_{j=1}^n λ_jh_j(p)
$$

# フィールド

  * `co::CO`, `μ::T`, `λ::T` は前述の通りで、`T` はベクトル型を表します。

# コンストラクタ

```
LagrangianCost(co, μ, λ)
```

固定された双対変数を持つラグランジアンのファンクタを作成します。

# 例

ラグランジアン $\mathcal L$ を直接評価したい場合は、次のように呼び出すこともできます。

```
LagrangianCost(co, μ, λ)(M,p)
```
