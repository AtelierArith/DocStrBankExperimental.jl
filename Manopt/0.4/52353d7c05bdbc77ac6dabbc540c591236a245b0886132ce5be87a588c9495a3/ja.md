```
AugmentedLagrangianCost{CO,R,T} <: AbstractConstrainedFunctor
```

拡張ラグランジアンに関連するパラメータ $ρ ∈ ℝ$, $μ ∈ ℝ^m$, $λ ∈ ℝ^n$ を格納します。これは [`ConstrainedManifoldObjective`](@ref) `co` に関連しています。

この構造体は、内部の [`ConstrainedManifoldObjective`](@ref) に基づいて、ソルバー内でコスト関数として使用できるファンクタ `(M,p) -> v` でもあります。計算されるのは次の式です。

$$
\mathcal L_\rho(p, μ, λ)
= f(x) + \frac{ρ}{2} \biggl(
    \sum_{j=1}^n \Bigl( h_j(p) + \frac{λ_j}{ρ} \Bigr)^2
    +
    \sum_{i=1}^m \max\Bigl\{ 0, \frac{μ_i}{ρ} + g_i(p) \Bigr\}^2
\Bigr)
$$

## フィールド

  * `co::CO`, `ρ::R`, `μ::T`, `λ::T` は、式で言及されているように、$R$ は使用される数値型、$T$ はベクトル型です。

# コンストラクタ

```
AugmentedLagrangianCost(co, ρ, μ, λ)
```
