```
GrB_BinaryOp_new(op, fn, ztype, xtype, ytype)
```

指定されたユーザー定義関数とその型でGraphBLASの二項演算子を初期化します。関数は2つの値(x, y)を受け取り、出力(z)を返す必要があります。f(x, y) = z。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> V = GrB_Vector{Float64}()
GrB_Vector{Float64}

julia> GrB_Vector_new(V, GrB_FP64, 4)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 0, 3, 3]; X = [2.1, 3.2, 4.5, 5.0]; n = 4;  # 位置0と3に2つの値

julia> dup = GrB_BinaryOp()  # dupは、ベクトル内の同じ位置に重複する値が存在する場合に適用される二項演算子
GrB_BinaryOp

julia> function ADD(b, c)
           return b+c
       end
ADD (generic function with 1 method)

julia> GrB_BinaryOp_new(dup, ADD, GrB_FP64, GrB_FP64, GrB_FP64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_build(V, I, X, n, dup)
GrB_SUCCESS::GrB_Info = 0

julia> @GxB_Vector_fprint(V, GxB_COMPLETE) # 位置0と3に格納される値は重複する値の合計になります

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
