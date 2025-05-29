```
GrB_Matrix_nrows(A)
```

Return the number of rows in a matrix if successful. Else return `GrB_Info` error code.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> MAT = GrB_Matrix{Int8}()
GrB_Matrix{Int8}

julia> GrB_Matrix_new(MAT, GrB_INT8, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_nrows(MAT)
0x0000000000000004
```
