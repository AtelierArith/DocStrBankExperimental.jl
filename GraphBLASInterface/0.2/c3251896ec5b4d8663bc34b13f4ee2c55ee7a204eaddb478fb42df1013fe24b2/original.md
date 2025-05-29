```
GrB_Col_assign(C, Mask, accum, u, I, ni, j, desc)
```

Assign the contents of a vector to a subset of elements in one column of a matrix. Note that since the output cannot be transposed, a different variant of assign is provided to assign to a row of matrix.

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

julia> GrB_Col_assign(A, GrB_NULL, GrB_NULL, u, ZeroBasedIndex[1, 2], 2, ZeroBasedIndex(0), GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_wait()
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Matrix_fprint(A, GxB_COMPLETE)

GraphBLAS matrix: A
nrows: 4 ncols: 4 max # entries: 7
format: standard CSR vlen: 4 nvec_nonempty: 3 nvec: 4 plen: 4 vdim: 4
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 5
row: 0 : 2 entries [0:1]
    column 1: int64 10
    column 2: int64 20
row: 1 : 1 entries [2:2]
    column 0: int64 5
row: 2 : 2 entries [3:4]
    column 0: int64 6
    column 2: int64 40
```
