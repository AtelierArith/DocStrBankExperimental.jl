```
GrB_Matrix_reduce_BinaryOp(w, mask, accum, op, A, desc)
```

行列のエントリをベクトルに縮約します。デフォルトでは、これらのメソッドは w(i) = sum(A(i,:)) となる列ベクトル w を計算します。ここで「sum」は可換かつ結合的な二項演算子です。A は転置可能で、行ではなく列を縮約します。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> A = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(A, GrB_INT64, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 0, 2, 2]; J = ZeroBasedIndex[1, 2, 0, 2]; X = [10, 20, 30, 40]; n = 4;

julia> GrB_Matrix_build(A, I, J, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> w = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(w, GrB_INT64, 4)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_reduce_BinaryOp(w, GrB_NULL, GrB_NULL, GrB_TIMES_INT64, A, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(w, GxB_COMPLETE)

GraphBLAS vector: w
nrows: 4 ncols: 1 max # entries: 2
format: standard CSC vlen: 4 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 2
column: 0 : 2 entries [0:1]
    row 0: int64 200
    row 2: int64 1200
```
