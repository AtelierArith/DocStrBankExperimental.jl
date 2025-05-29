```
global_rep(λY::GlobalSection{T, AT}, Δ::AbstractMatrix{T}) where {T, AT<:GrassmannManifold{T}}
```

`Δ`（`Y`の接空間の要素）を[`GrassmannLieAlgHorMatrix`](@ref)のインスタンスとして表現します。

[`GrassmannManifold`](@ref)のためのメソッド`global_rep`は、[`StiefelManifold`](@ref)のためのものと似ています。

# 例

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: _round
import Random 

Random.seed!(123)

Y = rand(GrassmannManifold, 6, 3)
Δ = rgrad(Y, randn(6, 3))
λY = GlobalSection(Y)

_round(global_rep(λY, Δ); digits = 3)

# 出力

6×6 GrassmannLieAlgHorMatrix{Float64, Matrix{Float64}}:
  0.0     0.0     0.0     0.981  -2.058   0.4
  0.0     0.0     0.0    -0.424   0.733  -0.919
  0.0     0.0     0.0    -1.815   1.409   1.085
 -0.981   0.424   1.815   0.0     0.0     0.0
  2.058  -0.733  -1.409   0.0     0.0     0.0
 -0.4     0.919  -1.085   0.0     0.0     0.0
```
