```
GrB_Matrix_dup(C, A)
```

別の行列と同じドメイン、次元、および内容を持つ新しい行列を初期化します。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> MAT = GrB_Matrix{Int8}()
GrB_Matrix{Int8}

julia> GrB_Matrix_new(MAT, GrB_INT8, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[1, 2, 2, 2, 3]; J = ZeroBasedIndex[1, 2, 1, 3, 3]; X = Int8[2, 3, 4, 5, 6]; n = 5;

julia> GrB_Matrix_build(MAT, I, J, X, n, GrB_FIRST_INT8)
GrB_SUCCESS::GrB_Info = 0

julia> B = GrB_Matrix{Int8}()
GrB_Matrix{Int8}

julia> GrB_Matrix_dup(B, MAT)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Matrix_fprint(B, GxB_COMPLETE)

GraphBLAS 行列: B
行数: 4 列数: 4 最大エントリ数: 5
フォーマット: 標準 CSR vlen: 4 nvec_nonempty: 3 nvec: 4 plen: 4 vdim: 4
ハイパー比 0.0625
GraphBLAS 型:  int8_t サイズ: 1
エントリ数: 5
行: 1 : 1 エントリ [0:0]
    列 1: int8 2
行: 2 : 3 エントリ [1:3]
    列 1: int8 4
    列 2: int8 3
    列 3: int8 5
行: 3 : 1 エントリ [4:4]
    列 3: int8 6
```
