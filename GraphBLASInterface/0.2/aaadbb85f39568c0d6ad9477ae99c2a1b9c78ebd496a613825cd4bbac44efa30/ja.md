```
GrB_eWiseAdd_Matrix_Semiring(C, Mask, accum, semiring, A, B, desc)
```

セミリングを使用して要素ごとの行列加算を計算します。セミリングの加算演算子が使用されます。 `C<Mask> = accum (C, A + B)`

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> A = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(A, GrB_INT64, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I1 = ZeroBasedIndex[0, 0, 2, 2]; J1 = ZeroBasedIndex[1, 2, 0, 2]; X1 = [10, 20, 30, 40]; n1 = 4;

julia> GrB_Matrix_build(A, I1, J1, X1, n1, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> B = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(B, GrB_INT64, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I2 = ZeroBasedIndex[0, 0, 2]; J2 = ZeroBasedIndex[3, 2, 0]; X2 = [15, 16, 17]; n2 = 3;

julia> GrB_Matrix_build(B, I2, J2, X2, n2, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> C = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(C, GrB_INT64, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_eWiseAdd_Matrix_Semiring(C, GrB_NULL, GrB_NULL, GxB_PLUS_TIMES_INT64, A, B, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(C, GxB_COMPLETE)

GraphBLAS 行列: C 
行数: 4 列数: 4 最大エントリ数: 5
フォーマット: 標準 CSR vlen: 4 nvec_nonempty: 2 nvec: 4 plen: 4 vdim: 4
ハイパー比 0.0625
GraphBLAS 型:  int64_t サイズ: 8
エントリ数: 5 
行: 0 : 3 エントリ [0:2]
    列 1: int64 10
    列 2: int64 36
    列 3: int64 15
行: 2 : 2 エントリ [3:4]
    列 0: int64 47
    列 2: int64 40
```
