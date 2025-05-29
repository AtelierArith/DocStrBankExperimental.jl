```
GrB_Matrix_reduce(monoid, A, desc)
```

Reduce entries in a matrix to a scalar. All entries in the matrix are "summed" using the reduce monoid, which must be associative (otherwise the results are undefined). If the matrix has no entries, the result is the identity value of the monoid.

# Examples

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

julia> GrB_Matrix_reduce(GxB_MIN_INT64_MONOID, A, GrB_NULL)
10
```
