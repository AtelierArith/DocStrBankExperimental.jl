```
csadiff(x,p,q)
```

Generate long memory by using the moving average representation of the cross-sectional aggregated process using the fast Fourier algorithm. See [Vera-Valdes(2021)](https://www.mdpi.com/2225-1146/9/4/39) for details.

# Arguments

  * `x::Vector`: time series
  * `p::Float64`: first parameter of the cross-sectional aggregated process
  * `q::Float64`: second parameter of the cross-sectional aggregated process, which is related to the fractional difference parameter `d` by `q = 2(1-d)`

# Output

  * `dx::Vector`: time series with long memory

# Notes

`q` determines the long memory parameter of the cross-sectional aggregated process. The relation `q = 2(1-d)` holds, where `d` is the fractional difference parameter. We use autoregressive formulas to efficiently compute the coefficients of the moving average representation of the cross-sectional aggregated process. 

# Examples

```julia-repl
julia> csadiff(randn(100,1),1.2,1.4)
```
