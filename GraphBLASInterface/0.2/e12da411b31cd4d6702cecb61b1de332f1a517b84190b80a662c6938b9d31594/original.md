```
GrB_Col_extract(w, mask, accum, A, I, ni, j, desc)
```

Extract from one column of a matrix into a vector. With the transpose descriptor for the source matrix, elements of an arbitrary row of the matrix can be extracted with this function as well.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> MAT = GrB_Matrix{Int8}()
GrB_Matrix{Int8}

julia> GrB_Matrix_new(MAT, GrB_INT8, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[1, 2, 2, 2, 3]; J = ZeroBasedIndex[1, 2, 1, 3, 3]; X = Int8[23, 34, 43, 57, 61]; n = 5;

julia> GrB_Matrix_build(MAT, I, J, X, n, GrB_FIRST_INT8)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Matrix_fprint(MAT, GxB_COMPLETE)

GraphBLAS matrix: MAT
nrows: 4 ncols: 4 max # entries: 5
format: standard CSR vlen: 4 nvec_nonempty: 3 nvec: 4 plen: 4 vdim: 4
hyper_ratio 0.0625
GraphBLAS type:  int8_t size: 1
number of entries: 5
row: 1 : 1 entries [0:0]
    column 1: int8 23
row: 2 : 3 entries [1:3]
    column 1: int8 43
    column 2: int8 34
    column 3: int8 57
row: 3 : 1 entries [4:4]
    column 3: int8 61


julia> desc = GrB_Descriptor()
GrB_Descriptor

julia> GrB_Descriptor_new(desc)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Descriptor_set(desc, GrB_INP0, GrB_TRAN) # descriptor to transpose first input
GrB_SUCCESS::GrB_Info = 0

julia> out = GrB_Vector{Int8}()
GrB_Vector{Int8}

julia> GrB_Vector_new(out, GrB_INT8, 3)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Col_extract(out, GrB_NULL, GrB_NULL, MAT, ZeroBasedIndex[1, 2, 3], 3, ZeroBasedIndex(2), desc) # extract elements of row 2
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_extractTuples(out)[2]
3-element Array{Int8,1}:
 43
 34
 57
```
