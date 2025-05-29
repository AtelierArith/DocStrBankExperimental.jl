Creates an interpolating function for a Smolyak approximation given the sampling points, `y`, and the approximation `plan`. Returns an interpolating function.

# Signature

f = smolyak_interp(y,plan)

# Examples

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> f = smolyak_interp(y,splan)
julia> f([0.37,0.71])
0.5953026581237828

julia> g,mi = smolyak_grid(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> f = smolyak_interp(y,splan)
julia> f([0.37,0.71])
0.5549321821467206
```
