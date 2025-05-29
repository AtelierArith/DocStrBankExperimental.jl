```
pconvert(a::Abstractay{T,1}) where T<:Number
```

convert two-element array to PVector2D, and three-element array to PVector

## Examples

```jl
julia> pconvert([1.0, 2.0])
PVector2D{Float64}(1.0, 2.0)

julia> pconvert([1.0, 2.0, 3.0])
PVector{Float64}(1.0, 2.0, 3.0)
```
