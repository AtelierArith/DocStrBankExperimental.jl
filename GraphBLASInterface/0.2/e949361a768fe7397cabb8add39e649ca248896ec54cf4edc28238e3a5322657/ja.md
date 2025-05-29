```
GrB_Matrix_extract(C, Mask, accum, A, I, ni, J, nj, desc)
```

指定された行インデックスのセットと列インデックスのセットによって、大きな行列からサブ行列を抽出します。結果は、インデックスのセットのサイズと等しいサイズの行列です。

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

julia> @GxB_Matrix_fprint(MAT, GxB_COMPLETE)

GraphBLAS matrix: MAT
nrows: 4 ncols: 4 max # entries: 5
format: standard CSR vlen: 4 nvec_nonempty: 3 nvec: 4 plen: 4 vdim: 4
hyper_ratio 0.0625
GraphBLAS type:  int8_t size: 1
number of entries: 5
row: 1 : 1 entries [0:0]
    column 1: int8 2
row: 2 : 3 entries [1:3]
    column 1: int8 4
    column 2: int8 3
    column 3: int8 5
row: 3 : 1 entries [4:4]
    column 3: int8 6


julia> OUT = GrB_Matrix{Int8}()
GrB_Matrix{Int8}

julia> GrB_Matrix_new(OUT, GrB_INT8, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_extract(OUT, GrB_NULL, GrB_NULL, MAT, ZeroBasedIndex[1, 3], 2, ZeroBasedIndex[1, 3], 2, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_extractTuples(OUT)[3]
2-element Array{Int8,1}:
 2
 6
```
