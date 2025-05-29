```
marchingsquares(edge)
```

Return the midpoint of the edge, in a manner similar to the [marching squares algorithm](https://en.wikipedia.org/wiki/Marching_squares). Does not require any function evaluations.

# Examples

```jldoctest
julia> f(x) = 1 - sum(abs2, x); # unit circle

julia> BG = bisect(f, (0.0:1.0, 0.0:1.0); iterations=3);


julia> E = edges(BG)
8-element Vector{Tuple{Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 ((0.75, 0.0), (1.0, 0.0))
 ((0.75, 0.25), (1.0, 0.25))
 ((0.75, 0.5), (1.0, 0.5))
 ((0.75, 0.5), (0.75, 0.75))
 ((0.0, 0.75), (0.0, 1.0))
 ((0.25, 0.75), (0.25, 1.0))
 ((0.5, 0.75), (0.75, 0.75))
 ((0.5, 0.75), (0.5, 1.0))

julia> marchingsquares.(E)
8-element Vector{Tuple{Float64, Float64}}:
 (0.875, 0.0)
 (0.875, 0.25)
 (0.875, 0.5)
 (0.75, 0.625)
 (0.0, 0.875)
 (0.25, 0.875)
 (0.625, 0.75)
 (0.5, 0.875)
```
