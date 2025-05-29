Evaluates a Smolyak polynomial formed using Chebyshev basis functions, given the `weights` and a Smolyak polynomial. Returns a scalar.

# Signature

yhat = smolyak_evaluate(weights,polynomial)

# Example

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> p = smolyak_polynomial([0.37,0.71],mi,[1.0 1.0; 0.0 0.0])
julia> yhat = smolyak_evaluate(w,p)
0.5953026581237828
```
