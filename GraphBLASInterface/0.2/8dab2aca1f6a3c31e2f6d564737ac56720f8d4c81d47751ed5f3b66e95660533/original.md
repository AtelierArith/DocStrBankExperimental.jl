```
GrB_Row_assign(C, mask, accum, u, i, J, nj, desc)
```

Assign the contents of a vector to a subset of elements in one row of a matrix. Note that since the output cannot be transposed, a different variant of assign is provided to assign to a column of a matrix.

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

julia> u = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(u, GrB_INT64, 2)
GrB_SUCCESS::GrB_Info = 0

julia> I2 = ZeroBasedIndex[0, 1]; X2 = [5, 6]; n2 = 2;

julia> GrB_Vector_build(u, I2, X2, n2, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Row_assign(A, GrB_NULL, GrB_NULL, u, ZeroBasedIndex(0), ZeroBasedIndex[1, 3], 2, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_wait()
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Matrix_fprint(A, GxB_COMPLETE)

GraphBLAS matrix: A
nrows: 4 ncols: 4 max # entries: 7
format: standard CSR vlen: 4 nvec_nonempty: 2 nvec: 4 plen: 4 vdim: 4
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 5
row: 0 : 3 entries [0:2]
    column 1: int64 5
    column 2: int64 20
    column 3: int64 6
row: 2 : 2 entries [3:4]
    column 0: int64 30
    column 2: int64 40
```
