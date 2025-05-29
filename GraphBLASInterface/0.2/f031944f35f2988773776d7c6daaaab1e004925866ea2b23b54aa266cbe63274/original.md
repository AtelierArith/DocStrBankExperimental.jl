```
GrB_BinaryOp_new(op, fn, ztype, xtype, ytype)
```

Initialize a GraphBLAS binary operator with a specified user-defined function and its types. The function should take 2 values(x, y) & return an output(z), f(x, y) = z.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> V = GrB_Vector{Float64}()
GrB_Vector{Float64}

julia> GrB_Vector_new(V, GrB_FP64, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 0, 3, 3]; X = [2.1, 3.2, 4.5, 5.0]; n = 4;  # two values at position 0 and 3

julia> dup = GrB_BinaryOp()  # dup is a binary operator which is applied when duplicate values for the same location are present in the vector
GrB_BinaryOp

julia> function ADD(b, c)
           return b+c
       end
ADD (generic function with 1 method)

julia> GrB_BinaryOp_new(dup, ADD, GrB_FP64, GrB_FP64, GrB_FP64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_build(V, I, X, n, dup)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Vector_fprint(V, GxB_COMPLETE) # the value stored at position 0 and 3 will be the sum of the duplicate values

GraphBLAS vector: V
nrows: 4 ncols: 1 max # entries: 2
format: standard CSC vlen: 4 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS type:  double size: 8
number of entries: 2
column: 0 : 2 entries [0:1]
    row 0: double 5.3
    row 3: double 9.5
```
