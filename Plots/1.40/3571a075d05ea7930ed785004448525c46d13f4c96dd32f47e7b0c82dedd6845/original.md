```
histogram2d(x,y)
histogram2d!(x,y)
```

Plot a two-dimensional histogram.

# Arguments

  * `bins`: Number of bins (if an `Integer`) or bin edges (if an `AbtractVector`)
  * `weights`: Vector of weights for the values in `x`. Each entry of x contributes            its weight to the height of its bin.

# Example

```julia-repl
julia> histogram2d(randn(10_000),randn(10_000))
```
