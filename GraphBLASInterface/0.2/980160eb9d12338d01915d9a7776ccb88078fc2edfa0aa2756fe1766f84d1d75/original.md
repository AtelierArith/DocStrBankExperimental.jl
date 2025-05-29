```
GrB_Matrix_assign(C, Mask, accum, A, I, ni, J, nj, desc)
```

Assign values from one GraphBLAS matrix to a subset of a matrix as specified by a set of indices. The dimensions of the input matrix are the same size as the row and column index arrays provided.

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

julia> C = GrB_Matrix{Int64}()
GrB_Matrix{Int64}

julia> GrB_Matrix_new(C, GrB_INT64, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_assign(C, GrB_NULL, GrB_NULL, A, GrB_ALL, 4, GrB_ALL, 4, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_wait()
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Matrix_fprint(C, GxB_COMPLETE)

GraphBLAS matrix: C
nrows: 4 ncols: 4 max # entries: 4
format: standard CSR vlen: 4 nvec_nonempty: 2 nvec: 4 plen: 4 vdim: 4
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 4
row: 0 : 2 entries [0:1]
    column 1: int64 10
    column 2: int64 20
row: 2 : 2 entries [2:3]
    column 0: int64 30
    column 2: int64 40
```
