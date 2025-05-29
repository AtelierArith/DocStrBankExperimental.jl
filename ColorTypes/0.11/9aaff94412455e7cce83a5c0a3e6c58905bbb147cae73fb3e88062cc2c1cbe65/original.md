```
ColorTypes.nan(C)
```

Return a color instance of the specified type in which all components are NaN.

# Examples

```jldoctest; setup = :(using ColorTypes)
julia> ColorTypes.nan(RGB{Float32})
RGB{Float32}(NaN32,NaN32,NaN32)

julia> ColorTypes.nan(AHSV{Float64})
AHSV{Float64}(NaN,NaN,NaN,NaN)
```
