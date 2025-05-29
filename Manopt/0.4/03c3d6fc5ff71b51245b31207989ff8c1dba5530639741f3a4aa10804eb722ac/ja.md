```
AugmentedLagrangianGrad{CO,R,T} <: AbstractConstrainedFunctor{T}
```

拡張ラグランジアンに関連するパラメータ $ρ ∈ ℝ$, $μ ∈ ℝ^m$, $λ ∈ ℝ^n$ を格納します。これは [`ConstrainedManifoldObjective`](@ref) `co` に関連しています。

この構造体は、次の2つの形式でファンクタでもあります。

  * `(M, p) -> X` は、割り当て方式で勾配を計算します。
  * `(M, X, p)` は、インプレース方式で勾配を計算します。

さらに、この勾配は、制約付き目的関数の内部勾配呼び出しの `range` を指定するための位置引数を最後に受け入れます。

内部の [`ConstrainedManifoldObjective`](@ref) に基づいており、勾配 $\operatorname{grad} \mathcal L_{ρ}(p, μ, λ)$ を計算します。詳細は [`AugmentedLagrangianCost`](@ref) を参照してください。

## フィールド

  * `co::CO`, `ρ::R`, `μ::T`, `λ::T` は、式で言及されているように、$R$ は使用される数値型、$T$ はベクトル型です。

# コンストラクタ

```
AugmentedLagrangianGrad(co, ρ, μ, λ)
```
