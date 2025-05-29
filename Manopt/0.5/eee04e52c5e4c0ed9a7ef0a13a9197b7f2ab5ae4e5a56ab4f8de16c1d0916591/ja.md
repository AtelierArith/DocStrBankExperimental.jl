```
LagrangianGradient{CO,T}
```

制約付き多様体目的関数 [`ConstrainedManifoldObjective`](@ref) `co` の変数 $p$ に関するラグランジアンの勾配。式は次のようになります。

$$
\operatorname{grad}_p \mathcal L(p; μ, λ)
= \operatorname{grad} f(p) +  \sum_{i=1}^m μ_i \operatorname{grad} g_i(p) + \sum_{j=1}^n λ_j \operatorname{grad} h_j(p)
$$

# フィールド

  * `co::CO`, `μ::T`, `λ::T` で、ここで `T` はベクトル型を表します。

# コンストラクタ

```
LagrangianGradient(co, μ, λ)
```

固定された双対変数を持つラグランジアンのファンクタを作成します。

# 例

ラグランジアンの勾配 $\operatorname{grad}_p \mathcal L$ を直接評価したい場合は、`LagrangianGradient(co, μ, λ)(M,p)` またはインプレースバリアントのために `LagrangianGradient(co, μ, λ)(M,X,p)` を呼び出すこともできます。
