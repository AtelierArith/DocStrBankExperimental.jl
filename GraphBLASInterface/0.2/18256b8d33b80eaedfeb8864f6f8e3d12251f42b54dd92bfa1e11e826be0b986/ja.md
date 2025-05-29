```
GrB_Vector_size(v)
```

ベクトルのサイズを返します。成功しなかった場合は `GrB_Info` エラーコードを返します。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> V = GrB_Vector{Float64}()
GrB_Vector{Float64}

julia> GrB_Vector_new(V, GrB_FP64, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 2, 3]; X = [2.1, 3.2, 4.4]; n = 3;

julia> GrB_Vector_build(V, I, X, n, GrB_FIRST_FP64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_size(V)
0x0000000000000004
```
