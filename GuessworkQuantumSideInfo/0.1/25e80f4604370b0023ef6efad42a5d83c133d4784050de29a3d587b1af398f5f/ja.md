```
bra([T = Float64], i::Integer, d::Integer) -> SparseVector{Complex{T}}'
```

次元 `d` における `i` 番目の計算基底ベクトルに関連するブラを表す双対ベクトルを作成します。

## 例

```jldoctest
julia> bra(1,2)
1×2 LinearAlgebra.Adjoint{Complex{Float64},SparseVector{Complex{Float64},Int64}}:
 1.0-0.0im  0.0-0.0im

julia> collect(ans)
1×2 Array{Complex{Float64},2}:
 1.0-0.0im  0.0-0.0im
```
