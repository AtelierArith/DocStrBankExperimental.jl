```
fracdiff(x,d::Int)
```

Compute the first or null difference of a time series `x`. Multiple dispatch is used to return the same input or call the function `diff` from the Julia standard library if `d=1` or `d=0`, respectively.

# Arguments

  * `x::Vector`: time series
  * `d::Int64`: difference parameter

# Output

  * `dx::Vector`: first or null difference of `x`

# Examples

```julia-repl
julia> fracdiff(randn(100,1),1)
```
