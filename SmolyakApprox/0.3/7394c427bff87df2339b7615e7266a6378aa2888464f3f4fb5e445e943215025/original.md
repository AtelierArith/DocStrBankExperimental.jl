Evaluates a Smolyak polynomial formed using piecewise linear basis functions, given the `weights`, the `point` at which to evaluate the polynomial, approximation `grid`, the `multi_index`, and the approximation `domain`  (defaults to [1.0,-1.0]^d).  Returns a scalar.

# Signature

yhat = smolyak*pl,evaluate(weights,point,grid,multi*index,domain)

# Example

```
julia> g,mi = smolyak_grid(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> w = smolyak_pl_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
julia> yhat = smolyak_pl_evaluate(w,[0.37,0.71],g,mi,[1.0 1.0; 0.0 0.0])
0.5549321821467206
```
