Uses multi-threading to compute the weights in a Smolyak polynomial approximation formed using piecewise linear basis functions given the approximation sample, `y`, the approximation `grid`, the `multi_index`,  and the approximation `domain` (defaults to [-1.0,1.0]^d).  Returns a vector containing the weights in the  Smolyak polynomial.

# Signature

w = smolyak*pl*weights*threaded(y,grid,multi*index,domain)

# Example

```
julia> g,mi = smolyak_grid(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> w = smolyak_pl_weights_threaded(y,g,mi,[1.0 1.0; 0.0 0.0])
```
