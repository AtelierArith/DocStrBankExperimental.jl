Computes the hessian a Smolyak polynomial formed using Chebyshev basis functions, given the `weights`, the `point` at which to evaluate the polynomial, the `multi_index`, and the approximation `domain`.   Returns a matrix.

# Signature

hess = smolyak*hessian(weights,point,multi*index,domain)

# Example

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> hess = smolyak_hessian(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
[ -2.53475  1.06753
   1.06753  0.199234]
```
