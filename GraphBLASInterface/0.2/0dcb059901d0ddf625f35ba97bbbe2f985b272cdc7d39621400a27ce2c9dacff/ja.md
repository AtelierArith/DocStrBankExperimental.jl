```
GrB_mxv(w, mask, accum, semiring, A, u, desc)
```

行列を半環上のベクトルに掛け算します。結果はベクトルです。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> A = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(A, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I1 = ZeroBasedIndex[0, 0, 1]; J1 = ZeroBasedIndex[0, 1, 1]; X1 = [10, 20, 30]; n1 = 3;

julia> GrB_Matrix_build(A, I1, J1, X1, n1, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> u = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(u, GrB_INT64, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I2 = ZeroBasedIndex[0, 1]; X2 = [5, 6]; n2 = 2;

julia> GrB_Vector_build(u, I2, X2, n2, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> w = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(w, GrB_INT64, 2)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_mxv(w, GrB_NULL, GrB_NULL, GxB_PLUS_TIMES_INT64, A, u, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(w, GxB_COMPLETE)

GraphBLAS ベクトル: w 
nrows: 2 ncols: 1 max # entries: 2
format: standard CSC vlen: 2 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS 型:  int64_t size: 8
GrB_mxm, vxm, または mxv に使用された最後のメソッド: dot
エントリの数: 2 
列: 0 : 2 エントリ [0:1]
    行 0: int64 170
    行 1: int64 180
```
