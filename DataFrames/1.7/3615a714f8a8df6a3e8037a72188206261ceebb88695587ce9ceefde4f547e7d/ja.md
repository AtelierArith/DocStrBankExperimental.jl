```
ncol(df::AbstractDataFrame)
```

`AbstractDataFrame` `df` の列数を返します。

関連情報としては [`nrow`](@ref)、[`size`](@ref) があります。

# 例

```jldoctest
julia> df = DataFrame(i=1:10, x=rand(10), y=rand(["a", "b", "c"], 10));

julia> ncol(df)
3
```
