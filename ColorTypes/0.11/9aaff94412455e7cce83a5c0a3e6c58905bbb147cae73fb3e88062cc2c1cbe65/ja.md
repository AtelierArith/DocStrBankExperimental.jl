```
ColorTypes.nan(C)
```

指定された型のすべてのコンポーネントがNaNである色のインスタンスを返します。

# 例

```jldoctest; setup = :(using ColorTypes)
julia> ColorTypes.nan(RGB{Float32})
RGB{Float32}(NaN32,NaN32,NaN32)

julia> ColorTypes.nan(AHSV{Float64})
AHSV{Float64}(NaN,NaN,NaN,NaN)
```
