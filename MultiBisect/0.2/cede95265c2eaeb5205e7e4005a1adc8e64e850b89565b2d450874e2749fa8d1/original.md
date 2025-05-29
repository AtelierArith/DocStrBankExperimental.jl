```
interpolate(BG::BisectionGrid{T, N}) where {T, N}
```

Compute the roots along all bracketing edges of `BG` with a linear approximation using precomputed function evaluations. Equivalent to `interpolate(linearroot(f), BG)`, but does not require re-evaluating the function at each edge.

# Examples

```jldoctest julia> f(x) = 1 - sum(abs2, x); # unit circle

julia> BG = bisect(f, (0.0:1.0, 0.0:1.0); iterations=3);

julia> interpolate(linearroot(f), BG) 8-element Vector{Tuple{Float64, Float64}}:  (1.0, 0.0)  (0.9642857142857143, 0.25)  (0.8571428571428571, 0.5)  (0.75, 0.65)  (0.0, 1.0)  (0.25, 0.9642857142857143)  (0.65, 0.75)  (0.5, 0.8571428571428571)

julia> interpolate(BG) 8-element Vector{Tuple{Float64, Float64}}:  (1.0, 0.0)  (0.9642857142857143, 0.25)  (0.8571428571428571, 0.5)  (0.75, 0.65)  (0.0, 1.0)  (0.25, 0.9642857142857143)  (0.65, 0.75)  (0.5, 0.8571428571428571)
