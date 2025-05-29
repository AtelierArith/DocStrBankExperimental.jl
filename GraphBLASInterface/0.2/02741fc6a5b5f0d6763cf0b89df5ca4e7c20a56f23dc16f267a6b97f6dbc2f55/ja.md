```
GrB_Matrix_reduce(monoid, A, desc)
```

行列のエントリをスカラーに減少させます。行列内のすべてのエントリは、結合的でなければならないreduceモノイドを使用して「合計」されます（そうでない場合、結果は未定義です）。行列にエントリがない場合、結果はモノイドの単位値です。

# 例

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

julia> GrB_Matrix_reduce(GxB_MIN_INT64_MONOID, A, GrB_NULL)
10
```
