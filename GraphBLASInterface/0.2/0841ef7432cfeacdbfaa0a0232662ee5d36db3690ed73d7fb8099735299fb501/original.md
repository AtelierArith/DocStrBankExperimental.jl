```
GrB_Vector_setElement(w, x, i)
```

Set one element of a vector to a given value, w[i] = x.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> V = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(V, GrB_INT64, 5)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[1, 2, 4]; X = [2, 32, 4]; n = 3;

julia> GrB_Vector_build(V, I, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_extractElement(V, ZeroBasedIndex(2))
32

julia> GrB_Vector_setElement(V, 7, ZeroBasedIndex(2))
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_extractElement(V, ZeroBasedIndex(2))
7
```
