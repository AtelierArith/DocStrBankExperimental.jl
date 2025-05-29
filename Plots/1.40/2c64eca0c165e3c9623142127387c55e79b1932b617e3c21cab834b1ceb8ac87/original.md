```
hexbin(x,y)
hexbin!(x,y)
```

Make a hexagonal binning plot (a histogram of the observations `(x[i],y[i])` with hexagonal bins).

# Example

```julia-repl
julia> hexbin(randn(10_000), randn(10_000))
```
