Computes the partial derivative of a full Smolyak polynomial formed using Chebyshev basis functions, given the  `weights`, the `point` at which to evaluate the polynomial, the `multi_index`, the approximation  `domain`, and the index of the variable to differentiate with respect to, `pos`. Returns a scalar.

# Signature

deriv = smolyak*derivative*full(weights,point,multi_index,domain,pos)

# Example

```
julia> g,mi = smolyak_grid_full(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights_full(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> deriv1 = smolyak_derivative_full(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0],1)
0.4036816953853277
julia> deriv2 = smolyak_derivative_full(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0],2)
0.5250627466157655
```
