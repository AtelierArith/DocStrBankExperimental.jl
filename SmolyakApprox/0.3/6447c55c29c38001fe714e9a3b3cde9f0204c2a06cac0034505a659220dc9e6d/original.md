Creates an interpolating function to compute the hessian of a Smolyak polynomial given the sampling points, `y`, and the approximation `plan`.  Returns an interpolating function.

# Signature

hess = smolyak_hessian(y,plan)

# Example

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> hess = smolyak_hessian(y,splan)
julia> hess([0.37,0.71])
[-2.53475  1.06753
  1.06753  0.199234]
```
