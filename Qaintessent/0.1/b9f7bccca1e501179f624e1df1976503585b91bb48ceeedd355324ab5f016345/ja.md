```
sparse_matrix(cg::CircuitGate{M,G}, N::Integer=0) where {M,G <: AbstractGate}
```

は、`N`量子ビットの状態ベクトルに適用できる[CircuitGate](@ref)オブジェクトの行列表現を返します。`N`は次のように設定できます。

# 例

```jldoctest
julia> cg = circuit_gate(2, Y, 1);
julia> sparse_matrix(cg)
4×4 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 4 stored entries:
  [1, 1]  =  1.0+0.0im
  [4, 2]  =  0.0+1.0im
  [3, 3]  =  1.0+0.0im
  [2, 4]  =  0.0-1.0im
```
