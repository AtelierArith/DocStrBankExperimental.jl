```
nrow(df::AbstractDataFrame)
```

`AbstractDataFrame` `df` の行数を返します。

関連: [`ncol`](@ref), [`size`](@ref).

# 例

```jldoctest
julia> df = DataFrame(i=1:10, x=rand(10), y=rand(["a", "b", "c"], 10));

julia> nrow(df)
10
```
