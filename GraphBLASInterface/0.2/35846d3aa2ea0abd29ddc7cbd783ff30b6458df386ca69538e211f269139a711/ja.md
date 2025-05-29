```
GrB_Vector_extract(w, mask, accum, u, I, ni, desc)
```

指定されたインデックスのセットによって、大きなベクトルからサブベクトルを抽出します。結果は、インデックスの数と等しいサイズのベクトルです。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> V = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(V, GrB_INT64, 5)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[1, 2, 4]; X = [15, 32, 84]; n = 3;

julia> GrB_Vector_build(V, I, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Vector_fprint(V, GxB_COMPLETE)

GraphBLAS vector: V
nrows: 5 ncols: 1 max # entries: 3
format: standard CSC vlen: 5 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 3
column: 0 : 3 entries [0:2]
    row 1: int64 15
    row 2: int64 32
    row 4: int64 84


julia> W = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(W, GrB_INT64, 2)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_extract(W, GrB_NULL, GrB_NULL, V, ZeroBasedIndex[1, 4], 2, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_extractTuples(W)[2]
2-element Array{Int64,1}:
 15
 84
```
