```julia
rescale(y, min::Number=0, max::Number=1)
```

Rescale a collection of numbers `y` between a new minimum `min` and new maximum `max`

### Examples

```julia
julia> rescale(1:5)
5-element Vector{Float64}:
0.0
0.25
0.5
0.75
1.0

julia> rescale(1:5, -1, 0)
5-element Vector{Float64}:
-1.0
-0.75
-0.5
-0.25
0.0
```
