```
ftuple(args...; kwargs...)
```

与えられた位置引数とキーワード引数から[`FrankenTuple`](@ref)を構築します。

# 例

```jldoctest
julia> ftuple(1, 2)
FrankenTuple((1, 2), NamedTuple())

julia> ftuple(1, 2, a=3, b=4)
FrankenTuple((1, 2), (a = 3, b = 4))
```
