```
csa_gen(T::Int,N::Int,p,q;t=0.01;μ=0,σ=1)
```

Generate a time series with long memory parameter `q` and length `T` using the cross-sectional aggregation of 'N' AR(1) processes à la Granger (1980).

# Arguments

  * `T::Int`: length of the time series
  * `N::Int`: number of AR(1) processes
  * `p::Float64`: first parameter of the cross-sectional aggregated process
  * `q::Float64`: second parameter of the cross-sectional aggregated process, which is related to the fractional difference parameter `d` by `q = 2(1-d)`

# Optional arguments

  * `t::Float64`: taper length
  * `μ::Float64`: mean of the time series
  * `σ::Float64`: standard deviation of the time series

# Notes

Multiple dispatch is used to generate the finite sample process if 'N' is included in the arguments.

# Output

  * `x::Vector`: time series with long memory

# Examples

```julia-repl
julia> csa_gen(100,100,1.2,1.4)
```
