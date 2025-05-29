" Computes the hessian of a complete Chebyshev polynomial evaluated at `x``, given the`$weights$`, the polynomial`$order$`, and the`$domain$`. 

# Signature

h = chebyshev_hessian(weights,x,order,domain)

# Example

```
julia> weights = [1.66416      0.598458    -0.0237052   0.00272941
  0.26378      0.0948592   -0.00375743  0.0
 -0.0246176   -0.00885287   0.0         0.0
  0.00372291   0.0          0.0         0.0]
julia> x = [5.5,0.9]
julia> ord = 3
julia> dom = [9.0 1.5; 3.0 0.5]
julia> h = chebyshev_hessian(weights,x,ord,dom)
[-0.0118089   0.069178
  0.069178   -0.421668]
```
