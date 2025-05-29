```
AugmentedLagrangianCost{CO,R,T}
```

拡張ラグランジアンに関連するパラメータ $ρ ∈ ℝ$, $μ ∈ ℝ^m$, $λ ∈ ℝ^n$ を [`ConstrainedManifoldObjective`](@ref) `co` に格納します。

この構造体は、内部の [`ConstrainedManifoldObjective`](@ref) に基づいて、ソルバー内でコスト関数として使用できる関数 `(M,p) -> v` でもあります。

$$
\mathcal L_\rho(p, μ, λ)
= f(x) + \frac{ρ}{2} \biggl(
    \sum_{j=1}^n \Bigl( h_j(p) + \frac{λ_j}{ρ} \Bigr)^2
    +
    \sum_{i=1}^m \max\Bigl\{ 0, \frac{μ_i}{ρ} + g_i(p) \Bigr\}^2
\Bigr)
$$

## フィールド

  * `co::CO`, `ρ::R`, `μ::T`, `λ::T` は、式で述べたように、$R$ は使用される数値型、$T$ はベクトル型です。

# コンストラクタ

```
AugmentedLagrangianCost(co, ρ, μ, λ)
```
