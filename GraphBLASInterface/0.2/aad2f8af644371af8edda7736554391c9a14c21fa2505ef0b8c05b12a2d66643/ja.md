```
GrB_Matrix_setElement(C, X, I, J)
```

行列の1つの要素を指定された値に設定します。C[I][J] = X。

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

julia> GrB_Matrix_extractElement(MAT, ZeroBasedIndex(1), ZeroBasedIndex(1))
2

julia> GrB_Matrix_setElement(MAT, Int8(7), ZeroBasedIndex(1), ZeroBasedIndex(1))
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_extractElement(MAT, ZeroBasedIndex(1), ZeroBasedIndex(1))
7
```
