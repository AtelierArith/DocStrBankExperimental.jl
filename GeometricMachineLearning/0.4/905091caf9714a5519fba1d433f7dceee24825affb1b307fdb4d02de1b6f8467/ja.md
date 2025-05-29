```
global_rep(λY::GlobalSection{T, AT}, Δ::AbstractMatrix{T}) where {T, AT<:StiefelManifold{T}}
```

`Δ`（`Y`の接空間）を`StiefelLieAlgHorMatrix`のインスタンスとして表現します。

これは、$T_Y\mathcal{M}$の要素を$\mathfrak{g}^\mathrm{hor}$の要素にマッピングします。

これらの2つの空間は同型であり、その同型は次のように$\lambda(Y)\in{}G$を通じて確立されます：

$$
T_Y\mathcal{M} \to \mathfrak{g}^{\mathrm{hor}}, \Delta \mapsto \lambda(Y)^{-1}\Omega(Y, \Delta)\lambda(Y).
$$

また、[`GeometricMachineLearning.Ω`](@ref)も参照してください。

# 例

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: _round
import Random 

Random.seed!(123)

Y = rand(StiefelManifold, 6, 3)
Δ = rgrad(Y, randn(6, 3))
λY = GlobalSection(Y)

_round(global_rep(λY, Δ); digits = 3)

# 出力

6×6 StiefelLieAlgHorMatrix{Float64, SkewSymMatrix{Float64, Vector{Float64}}, Matrix{Float64}}:
  0.0     0.679   1.925   0.981  -2.058   0.4
 -0.679   0.0     0.298  -0.424   0.733  -0.919
 -1.925  -0.298   0.0    -1.815   1.409   1.085
 -0.981   0.424   1.815   0.0     0.0     0.0
  2.058  -0.733  -1.409   0.0     0.0     0.0
 -0.4     0.919  -1.085   0.0     0.0     0.0
```

# 実装

関数`global_rep`は、実際には全体のマップ$\lambda(Y)^{-1}\Omega(Y, \Delta)\lambda(Y)$を実行するのではなく、次のことを行います：

$$
\Delta \mapsto \mathrm{skew}(Y^T\Delta),
$$

小さな斜対称行列$A\in\mathcal{S}_\mathrm{skew}(n)$を取得するために、

$$
\Delta \mapsto (\lambda(Y)_{[1:N, n:N]}^T \Delta)_{[1:(N-n), 1:n]},
$$

任意の行列$B\in\mathbb{R}^{(N-n)\times{}n}$を取得するために。 ```
