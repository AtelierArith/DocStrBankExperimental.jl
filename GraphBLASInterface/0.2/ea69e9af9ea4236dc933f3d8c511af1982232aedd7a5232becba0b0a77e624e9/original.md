```
GrB_Vector_dup(w, u)
```

Initialize a vector with the same domain, size, and contents as another vector.

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

julia> B = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_dup(B, V)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Vector_fprint(B, GxB_COMPLETE)

GraphBLAS vector: B
nrows: 5 ncols: 1 max # entries: 3
format: standard CSC vlen: 5 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 3
column: 0 : 3 entries [0:2]
    row 1: int64 2
    row 2: int64 32
    row 4: int64 4
```
