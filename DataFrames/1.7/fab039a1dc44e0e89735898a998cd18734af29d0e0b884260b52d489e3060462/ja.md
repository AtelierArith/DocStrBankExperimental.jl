```
size(df::AbstractDataFrame[, dim])
```

`df`の行数と列数を含むタプルを返します。オプションで次元`dim`を指定することができ、`1`は行に、`2`は列に対応します。

参照: [`nrow`](@ref), [`ncol`](@ref)

# 例

```jldoctest
julia> df = DataFrame(a=1:3, b='a':'c');

julia> size(df)
(3, 2)

julia> size(df, 1)
3
```
