```
GrB_Vector_build(w, I, X, nvals, dup)
```

タプルから要素をベクターに格納します。

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

julia> @GxB_Vector_fprint(V, GxB_COMPLETE)

GraphBLAS ベクター: V
nrows: 4 ncols: 1 max # entries: 3
format: standard CSC vlen: 4 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS 型:  double size: 8
エントリの数: 3
列: 0 : 3 エントリ [0:2]
    行 0: double 2.1
    行 2: double 3.2
    行 3: double 4.4
```
