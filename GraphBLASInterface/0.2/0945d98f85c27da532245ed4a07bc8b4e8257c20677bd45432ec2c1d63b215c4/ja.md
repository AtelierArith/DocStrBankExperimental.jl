```
GrB_Vector_reduce(monoid, u, desc)
```

ベクトルのエントリをスカラーに縮約します。ベクトル内のすべてのエントリは、縮約モノイドを使用して「合計」されます。このモノイドは結合的でなければなりません（そうでない場合、結果は未定義です）。ベクトルにエントリがない場合、結果はモノイドの単位値になります。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> u = GrB_Vector{Int64}()
GrB_Vector{Int64}

julia> GrB_Vector_new(u, GrB_INT64, 5)
GrB_SUCCESS::GrB_Info = 0

julia> I = ZeroBasedIndex[0, 2, 4]; X = [10, 20, 30]; n = 3;

julia> GrB_Vector_build(u, I, X, n, GrB_FIRST_INT64)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_Vector_reduce(GxB_MAX_INT64_MONOID, u, GrB_NULL)
30
```
