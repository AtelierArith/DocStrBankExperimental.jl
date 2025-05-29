```
splitsign(BG::BisectionGrid)
```

Split the evaluated points of the bisection grid into a vector of positive points and a vector of negative points.

# Examples

```jldoctest
julia> BG = bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); iterations=2)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.5:1.0, 0.0:0.5:1.0)
  Grid points: 9
  Evaluations: 9
        Edges: 4

julia> posx, negx = splitsign(BG);


julia> posx
4-element Vector{Tuple{Float64, Float64}}:
 (0.0, 0.0)
 (0.5, 0.0)
 (0.0, 0.5)
 (0.5, 0.5)

julia> negx
5-element Vector{Tuple{Float64, Float64}}:
 (1.0, 0.0)
 (1.0, 0.5)
 (0.0, 1.0)
 (0.5, 1.0)
 (1.0, 1.0)
```
