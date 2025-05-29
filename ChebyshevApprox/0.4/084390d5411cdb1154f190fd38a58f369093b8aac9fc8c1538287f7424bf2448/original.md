Creates a function that evaluates the hessian of a Chebyshev polynomial evaluated at `x`, given the approximation sample `y` and an approximation `plan`.

# Signature

h = chebyshev_hessian(y,plan)

# Example

```
julia> nodes1 = nodes(5,:chebyshev_nodes,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_nodes,[1.5,0.5])
julia> g = Grid((nodes1,nodes2))
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> plan = CApproxPlan(g,ord,dom)
julia> h = chebyshev_hessian(y,plan)
julia> h([5.5,0.9])
[-0.0118667   0.0661025
  0.0661025  -0.42678]
```
