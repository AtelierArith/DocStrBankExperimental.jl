```
GrB_eWiseAdd_Matrix_Monoid(C, Mask, accum, monoid, A, B, desc)
```

モノイドを使用して要素ごとの行列加算を計算します。 `C<Mask> = accum (C, A + B)`

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

julia> mask = GrB_Matrix{Bool}()
GrB_Matrix{Bool}

julia> GrB_Matrix_new(mask, GrB_BOOL, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_build(mask, ZeroBasedIndex[0, 0], ZeroBasedIndex[1, 2], [true, true], 2, GrB_FIRST_BOOL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_eWiseAdd_Matrix_Monoid(C, mask, GrB_NULL, GxB_PLUS_INT64_MONOID, A, B, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(C, GxB_COMPLETE)

GraphBLAS 行列: C 
行数: 4 列数: 4 最大エントリ数: 5
フォーマット: 標準 CSR vlen: 4 nvec_nonempty: 1 nvec: 4 plen: 4 vdim: 4
ハイパー比 0.0625
GraphBLAS 型:  int64_t サイズ: 8
エントリ数: 2 
行: 0 : 2 エントリ [0:1]
    列 1: int64 10
    列 2: int64 36
```
