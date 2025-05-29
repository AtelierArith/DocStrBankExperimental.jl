```
GrB_Vector_assign(w, mask, accum, u, I, ni, desc)
```

指定されたインデックスのセットによってベクトルのサブセットにGraphBLASベクトルから値を割り当てます。入力ベクトルのサイズは提供されたインデックス配列と同じサイズです。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> w = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(w, GrB_INT64, 5)
GrB_SUCCESS::GrB_Info = 0

julia> u = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(u, GrB_INT64, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 1]; X = [10, 20]; n = 2;

julia> GrB_Vector_build(u, I, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_assign(w, GrB_NULL, GrB_NULL, u, [2, 4], 2, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_extractTuples(w)
(ZeroBasedIndex[ZeroBasedIndex(0x0000000000000002), ZeroBasedIndex(0x0000000000000004)], [10, 20])
```
