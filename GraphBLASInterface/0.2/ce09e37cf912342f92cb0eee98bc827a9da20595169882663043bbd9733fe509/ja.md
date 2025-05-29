```
GrB_Matrix_apply(C, Mask, accum, op, A, desc)
```

行列の要素の値を単項関数を使用して変換します。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> A = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(A, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 0, 1]; J = ZeroBasedIndex[0, 1, 1]; X = [10, 20, 30]; n = 3;

julia> GrB_Matrix_build(A, I, J, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> B = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(B, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_apply(B, GrB_NULL, GrB_NULL, GrB_AINV_INT64, A, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(B, GxB_COMPLETE)

GraphBLAS 行列: B
行数: 2 列数: 2 最大エントリ数: 3
フォーマット: 標準 CSR vlen: 2 nvec_nonempty: 2 nvec: 2 plen: 2 vdim: 2
ハイパー比 0.0625
GraphBLAS 型:  int64_t サイズ: 8
エントリ数: 3
行: 0 : 2 エントリ [0:1]
    列 0: int64 -10
    列 1: int64 -20
行: 1 : 1 エントリ [2:2]
    列 1: int64 -30
```
