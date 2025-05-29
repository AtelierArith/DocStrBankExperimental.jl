```
GrB_UnaryOp_new(op, fn, ztype, xtype)
```

Initialize a GraphBLAS unary operator with a specified user-defined function and its types. The function should take a single value(x) & return an output(z), f(x) = z.

# Examples

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> u = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(u, GrB_INT64, 3)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 2]; X = [10, 20]; n = 2;

julia> GrB_Vector_build(u, I, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> w = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(w, GrB_INT64, 3)
GrB_SUCCESS::GrB_Info = 0

julia> function NEG(a)
           return -a
       end
NEG (generic function with 1 method)

julia> negative = GrB_UnaryOp()
GrB_UnaryOp

julia> GrB_UnaryOp_new(negative, NEG, GrB_INT64, GrB_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_apply(w, GrB_NULL, GrB_NULL, negative, u, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_fprint(w, GxB_COMPLETE)

GraphBLAS vector: w 
nrows: 3 ncols: 1 max # entries: 2
format: standard CSC vlen: 3 nvec_nonempty: 1 nvec: 1 plen: 1 vdim: 1
hyper_ratio 0.0625
GraphBLAS type:  int64_t size: 8
number of entries: 2 
column: 0 : 2 entries [0:1]
    row 0: int64 -10
    row 2: int64 -20
```
