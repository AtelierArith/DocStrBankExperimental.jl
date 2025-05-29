```
GrB_Vector_assign(w, mask, accum, x, I, ni, desc)
```

Assign the same value to a specified subset of vector elements. With the use of `GrB_ALL`, the entire destination vector can be filled with the constant.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> w = GrB_Vector{Float64}()
GrB_Vector{Float64}

julia> GrB_Vector_new(w, GrB_FP64, 4)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_assign(w, GrB_NULL, GrB_NULL, 2.3, ZeroBasedIndex[0, 3], 2, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_extractTuples(w)
(ZeroBasedIndex[ZeroBasedIndex(0x0000000000000000), ZeroBasedIndex(0x0000000000000003)], [2.3, 2.3])
```
