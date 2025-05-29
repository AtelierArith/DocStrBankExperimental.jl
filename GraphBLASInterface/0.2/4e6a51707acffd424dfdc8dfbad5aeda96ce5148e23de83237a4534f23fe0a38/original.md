```
GrB_error()
```

Each GraphBLAS method and operation returns a `GrB_Info` error code. `GrB_error` returns additional information on the last error.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_init(GrB_NONBLOCKING)
GrB_INVALID_VALUE::GrB_Info = 5

julia> GrB_error()
GraphBLAS error: GrB_INVALID_VALUE
function: GrB_init (mode)
GrB_init must not be called twice
```
