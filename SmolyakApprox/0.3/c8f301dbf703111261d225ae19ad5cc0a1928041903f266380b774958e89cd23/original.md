Creates an interpolating function that uses multi-treading to compute the gradient of a Smolyak polynomial given the sampling points, `y`, and the approximation `plan`.  Returns an interpolating function.

# Signature

grad = smolyak*gradient*threaded(y,plan)

# Example

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> grad = smolyak_gradient_threaded(y,splan)
julia> grad([0.37,0.71])
[0.403682  0.525063]
```
