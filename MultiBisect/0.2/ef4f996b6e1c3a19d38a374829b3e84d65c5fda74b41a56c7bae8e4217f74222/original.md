```
linearroot(f, edge)
```

Construct a linear interpolation of `f` through `edge` and return its root. Requires two function evaluations.

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

julia> linearroot.(f, E)
8-element Vector{Tuple{Float64, Float64}}:
 (1.0, 0.0)
 (0.9642857142857143, 0.25)
 (0.8571428571428571, 0.5)
 (0.75, 0.65)
 (0.0, 1.0)
 (0.25, 0.9642857142857143)
 (0.65, 0.75)
 (0.5, 0.8571428571428571)
```
