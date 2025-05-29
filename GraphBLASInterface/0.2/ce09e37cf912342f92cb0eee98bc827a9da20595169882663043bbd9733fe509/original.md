```
GrB_Matrix_apply(C, Mask, accum, op, A, desc)
```

Compute the transformation of the values of the elements of a matrix using a unary function.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> A = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(A, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 0, 1]; J = ZeroBasedIndex[0, 1, 1]; X = [10, 20, 30]; n = 3;

julia> GrB_Matrix_build(A, I, J, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> B = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(B, GrB_INT64, 2, 2)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_apply(B, GrB_NULL, GrB_NULL, GrB_AINV_INT64, A, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(B, GxB_COMPLETE)

GraphBLAS matrix: B
nrows: 2 ncols: 2 max # entries: 3
format: standard CSR vlen: 2 nvec_nonempty: 2 nvec: 2 plen: 2 vdim: 2
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 3
row: 0 : 2 entries [0:1]
    column 0: int64 -10
    column 1: int64 -20
row: 1 : 1 entries [2:2]
    column 1: int64 -30
```
