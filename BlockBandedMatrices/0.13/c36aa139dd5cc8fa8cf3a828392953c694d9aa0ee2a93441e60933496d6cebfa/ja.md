```
BlockSkylineMatrix{T,LL,UU}(M::Union{UndefInitializer,UniformScaling,AbstractMatrix},
                            rows, cols, (l::LL, u::UU))
```

は、要素の型 `T` を持つ `sum(rows)`×`sum(cols)` のブロックバンド行列 `A` を返します。ブロックバンド幅は `(l,u)` であり、`A[Block(K,J)]` はサイズ `rows[K]`×`cols[J]` の `Matrix{T}` です。

`(l,u)` は、定数バンド幅のための整数であるか、乱れたバンドのための長さ `length(cols)` の整数ベクトルである可能性があります。後者の場合、`l` と `u` は各列のサブブロックバンドとスーパーブロックバンドの数を表します。

# 例

```jldoctest
julia> using LinearAlgebra, FillArrays

julia> BlockSkylineMatrix(I, [2,2,2,4], [1,2,3], ([2,0,1],[0,1,1]))
4×3-blocked 10×6 BlockSkylineMatrix{Bool, Vector{Bool}, BlockBandedMatrices.BlockSkylineSizes{Tuple{BlockArrays.BlockedOneTo{Int64, Vector{Int64}}, BlockArrays.BlockedOneTo{Int64, Vector{Int64}}}, Vector{Int64}, Vector{Int64}, BandedMatrices.BandedMatrix{Int64, Matrix{Int64}, Base.OneTo{Int64}}, Vector{Int64}}}:
 1  │  0  0  │  ⋅  ⋅  ⋅
 0  │  1  0  │  ⋅  ⋅  ⋅
 ───┼────────┼─────────
 0  │  0  1  │  0  0  0
 0  │  0  0  │  1  0  0
 ───┼────────┼─────────
 0  │  ⋅  ⋅  │  0  1  0
 0  │  ⋅  ⋅  │  0  0  1
 ───┼────────┼─────────
 ⋅  │  ⋅  ⋅  │  0  0  0
 ⋅  │  ⋅  ⋅  │  0  0  0
 ⋅  │  ⋅  ⋅  │  0  0  0
 ⋅  │  ⋅  ⋅  │  0  0  0

julia> BlockSkylineMatrix(Ones(9,6), [2,3,4], [1,2,3], ([2,0,0],[0,1,1]))
3×3-blocked 9×6 BlockSkylineMatrix{Float64, Vector{Float64}, BlockBandedMatrices.BlockSkylineSizes{Tuple{BlockArrays.BlockedOneTo{Int64, Vector{Int64}}, BlockArrays.BlockedOneTo{Int64, Vector{Int64}}}, Vector{Int64}, Vector{Int64}, BandedMatrices.BandedMatrix{Int64, Matrix{Int64}, Base.OneTo{Int64}}, Vector{Int64}}}:
 1.0  │  1.0  1.0  │   ⋅    ⋅    ⋅
 1.0  │  1.0  1.0  │   ⋅    ⋅    ⋅
 ─────┼────────────┼───────────────
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 1.0  │  1.0  1.0  │  1.0  1.0  1.0
 ─────┼────────────┼───────────────
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
 1.0  │   ⋅    ⋅   │  1.0  1.0  1.0
```
