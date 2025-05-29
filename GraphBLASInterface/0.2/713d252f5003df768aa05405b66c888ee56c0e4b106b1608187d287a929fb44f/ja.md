```
GrB_Matrix_assign(C, Mask, accum, x, I, ni, J, nj, desc)
```

指定された行列要素のサブセットに同じ値を割り当てます。`GrB_ALL`を使用することで、定数で全体の行列を埋めることができます。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> A = GrB_Matrix{Bool}()
GrB_Matrix{Bool}

julia> GrB_Matrix_new(A, GrB_BOOL, 4, 4)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Matrix_assign(A, GrB_NULL, GrB_NULL, true, ZeroBasedIndex[0, 1], 2, ZeroBasedIndex[0, 1], 2, GrB_NULL)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_wait()
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Matrix_fprint(A, GxB_COMPLETE)

GraphBLAS matrix: A
nrows: 4 ncols: 4 max # entries: 4
format: standard CSR vlen: 4 nvec_nonempty: 2 nvec: 4 plen: 4 vdim: 4
hyper_ratio 0.0625
GraphBLAS type:  bool size: 1
number of entries: 4
row: 0 : 2 entries [0:1]
    column 0: bool 1
    column 1: bool 1
row: 1 : 2 entries [2:3]
    column 0: bool 1
    column 1: bool 1
```
