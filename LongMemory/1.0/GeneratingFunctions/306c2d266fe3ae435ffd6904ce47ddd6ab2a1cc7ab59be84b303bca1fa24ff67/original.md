```
csa_gen(T::Int,p,q;μ=0,σ=1)
```

Generate a time series with long memory parameter `q` and length `T` using the cross-sectional aggregated process.  See [Vera-Valdes(2021)](https://www.mdpi.com/2225-1146/9/4/39) for details.

# Arguments

  * `T::Int`: length of the time series
  * `p::Float64`: first parameter of the cross-sectional aggregated process
  * `q::Float64`: second parameter of the cross-sectional aggregated process, which is related to the fractional difference parameter `d` by `q = 2(1-d)`

# Optional arguments

  * `μ::Float64`: mean of the time series
  * `σ::Float64`: standard deviation of the time series

# Output

  * `x::Vector`: time series with long memory

# Examples

```julia-repl
julia> csa_gen(100,1.2,1.4)
```
