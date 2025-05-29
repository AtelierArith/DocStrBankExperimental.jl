```
BlochMessiah <: Factorization
```

シンプレクティック行列 `S` のブロッホ-メサイア/オイラー分解の行列因子化タイプです。これは、対応する行列因子化関数 [`blochmessiah(_)`](@ref) の戻り値の型です。

`F::BlochMessiah` が因子化オブジェクトである場合、`O`、`values` および `Q` はそれぞれ `F.O`、`F.values`、および `F.Q` を介して取得できます。

分解を反復することで、`O`、`values`、および `Q` のコンポーネントがその順序で生成されます。

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
O factor:
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
 0.850651  -0.525731
 0.525731   0.850651
values:
1-element Vector{Float64}:
 1.618033988749895
Q factor:
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
  0.525731  0.850651
 -0.850651  0.525731

julia> isapprox(S, F.O * Diagonal(vcat(F.values, F.values .^ (-1))) * F.Q, atol = 1e-10)
true

julia> issymplectic(F.O, atol = 1e-10) && issymplectic(F.Q, atol = 1e-10)
true

julia> O, values, Q = F; # 反復による分解

julia> O == F.O && values == F.values && Q == F.Q
true
```
