```
ohlc(x,y::Vector{OHLC})
ohlc!(x,y::Vector{OHLC})
```

Make open-high-low-close plot. Each entry of y is represented by a vertical segment extending from the low value to the high value, with short horizontal segments on the left and right indicating the open and close values, respectively.

# Example

```julia-repl
julia> meanprices = cumsum(randn(100))
julia> y = OHLC[(p+rand(),p+1,p-1,p+rand()) for p in meanprices]
julia> ohlc(y)
```
