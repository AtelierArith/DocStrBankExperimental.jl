```
GrB_free(object)
```

GraphBLASオブジェクトを解放するための汎用メソッド。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> w = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> I = ZeroBasedIndex[0, 2, 4]; X = [10, 20, 30]; n = 3;

julia> GrB_Vector_new(w, GrB_INT64, 5)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_build(w, I, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(w, GxB_COMPLETE)

GraphBLASベクトル: w
nrows: 5 ncols: 1 max # entries: 3
format: standard CSC vlen: 5 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS型:  int64_t size: 8
エントリ数: 3
列: 0 : 3 entries [0:2]
    行 0: int64 10
    行 2: int64 20
    行 4: int64 30


julia> GrB_free(w)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(w, GxB_COMPLETE)

GraphBLASベクトル: w NULL
```
