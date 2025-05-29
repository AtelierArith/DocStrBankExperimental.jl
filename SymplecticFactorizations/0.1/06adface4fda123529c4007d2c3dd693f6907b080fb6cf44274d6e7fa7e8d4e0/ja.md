```
blochmessiah(form::SymplecticForm, S::AbstractMatrix) -> BlochMessiah
blochmessiah(S::Symplectic) -> BlochMessiah
```

シンプレクティック行列 `S` のブロッホ-メシア分解/オイラー分解を計算し、`BlockMessiah` オブジェクトを返します。

直交シンプレクティック行列 `O` と `Q`、および特異値 `values` はそれぞれ `F.O`、`F.Q`、`F.values` を介して取得できます。

分解を繰り返すことで、コンポーネント `O`、`values`、`Q` がその順序で得られます。

# 例

```
julia> S = Symplectic(BlockForm(1), [1. 1.; 0. 1.])
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
 1.0  1.0
 0.0  1.0

julia> issymplectic(S)
true

julia> F = blochmessiah(S)
BlochMessiah{Float64, Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}, Vector{Float64}}
O 因子:
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
 0.850651  -0.525731
 0.525731   0.850651
値:
1-element Vector{Float64}:
 1.618033988749895
Q 因子:
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
  0.525731  0.850651
 -0.850651  0.525731

julia> isapprox(S, F.O * Diagonal(vcat(F.values, F.values .^ (-1))) * F.Q, atol = 1e-10)
true

julia> issymplectic(F.O, atol = 1e-10) && issymplectic(F.Q, atol = 1e-10)
true

julia> O, values, Q = F; # 繰り返しによる分解

julia> O == F.O && values == F.values && Q == F.Q
true
```
