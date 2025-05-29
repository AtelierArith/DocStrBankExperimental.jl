```
GrB_Vector_reduce(monoid, u, desc)
```

Reduce entries in a vector to a scalar. All entries in the vector are "summed" using the reduce monoid, which must be associative (otherwise the results are undefined). If the vector has no entries, the result is the identity value of the monoid.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> u = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(u, GrB_INT64, 5)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 2, 4]; X = [10, 20, 30]; n = 3;

julia> GrB_Vector_build(u, I, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_reduce(GxB_MAX_INT64_MONOID, u, GrB_NULL)
30
```
