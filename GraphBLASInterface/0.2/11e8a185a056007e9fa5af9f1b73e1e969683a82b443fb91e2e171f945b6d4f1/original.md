```
GrB_Matrix_extractTuples(A, index_type)
```

Return tuples stored in a matrix if successful. Else return `GrB_Info` error code.

# Examples

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

julia> GrB_Matrix_extractTuples(MAT)
(ZeroBasedIndex[ZeroBasedIndex(0x0000000000000001), ZeroBasedIndex(0x0000000000000002), ZeroBasedIndex(0x0000000000000002), ZeroBasedIndex(0x0000000000000002), ZeroBasedIndex(0x0000000000000003)], ZeroBasedIndex[ZeroBasedIndex(0x0000000000000001), ZeroBasedIndex(0x0000000000000001), ZeroBasedIndex(0x0000000000000002), ZeroBasedIndex(0x0000000000000003), ZeroBasedIndex(0x0000000000000003)], Int8[2, 4, 3, 5, 6])
```
