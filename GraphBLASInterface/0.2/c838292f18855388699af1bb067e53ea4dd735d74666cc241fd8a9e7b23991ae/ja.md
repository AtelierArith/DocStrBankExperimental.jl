```
GrB_mxm(C, Mask, accum, semiring, A, B, desc)
```

行列を半環で別の行列と掛け算します。結果は行列です。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> A = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(A, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I1 = ZeroBasedIndex[0, 1]; J1 = ZeroBasedIndex[0, 1]; X1 = [10, 20]; n1 = 2;

julia> GrB_Matrix_build(A, I1, J1, X1, n1, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> B = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(B, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I2 = ZeroBasedIndex[0, 1]; J2 = ZeroBasedIndex[0, 1]; X2 = [5, 15]; n2 = 2;

julia> GrB_Matrix_build(B, I2, J2, X2, n2, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> C = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(C, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_mxm(C, GrB_NULL, GrB_NULL, GxB_PLUS_TIMES_INT64, A, B, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(C, GxB_COMPLETE)

GraphBLAS 行列: C 
行数: 2 列数: 2 最大エントリ数: 2
フォーマット: 標準 CSR vlen: 2 nvec_nonempty: 2 nvec: 2 plen: 2 vdim: 2
ハイパー比 0.0625
GraphBLAS 型:  int64_t サイズ: 8
GrB_mxm、vxm、またはmxvに使用された最後のメソッド: ヒープ
エントリ数: 2 
行: 0 : 1 エントリ [0:0]
    列 0: int64 50
行: 1 : 1 エントリ [1:1]
    列 1: int64 300
```
