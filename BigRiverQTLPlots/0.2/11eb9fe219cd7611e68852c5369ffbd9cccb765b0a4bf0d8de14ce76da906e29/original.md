```
pseudotick(mytick::Vector{Float64}) => Vector{Float64}
```

Returns coordinates of the new ticks. It returns the midpoints  between each consecutive pairs of value.

## Example

```julia
julia> vticks = [1,4,5,7] |> float;

julia> pseudoticks(vticks)
4-element Vector{Float64}:
 0.5
 2.5
 4.5
 6.0

```
