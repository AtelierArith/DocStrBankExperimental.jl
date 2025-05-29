Evaluates a hyperbolic cross polynomial formed using Chebyshev basis functions, given the `weights`, the  `point` at which to evaluate the polynomial, the `multi_index`, and the approximation `domain`  (defaults to [-1.0,1.0]^d).  Returns a scalar.

# Signatures

yhat = hyperbolic*cross*evaluate(weights,point,multi*index) yhat = hyperbolic*cross*evaluate(weights,point,multi*index,domain)

# Example

```
julia> g,mi = hyperbolic_cross_grid(chebyshev_extrema,2,3,5,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = hyperbolic_cross_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> yhat = hyperbolic_cross_evaluate(w,[0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
0.6100559317314179
```
