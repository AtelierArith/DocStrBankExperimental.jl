Evaluates a hyperbolic cross polynomial formed using Chebyshev basis functions, given the `weights`and the hyperbolic cross polynomial.  Returns a scalar.

# Signature

yhat = hyperbolic*cross*evaluate(weights,poly)

# Example

```
julia> g,mi = hyperbolic_cross_grid(chebyshev_extrema,2,3,5,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = hyperbolic_cross_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> hpoly = hyperbolic_cross_polynomial([0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
julia> yhat = hyperbolic_cross_evaluate(w,hpoly)
0.6100559317314179
```
