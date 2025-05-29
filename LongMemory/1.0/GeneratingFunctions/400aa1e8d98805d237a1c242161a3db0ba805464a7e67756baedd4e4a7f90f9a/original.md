```
fi(T,d;μ=0,σ=1)
```

Generate a time series with long memory parameter `d` and length `T` using the fractional difference filter.

# Arguments

  * `T::Int`: length of the time series
  * `d::Float64`: fractional difference parameter

# Optional arguments

  * `μ::Float64`: mean of the time series
  * `σ::Float64`: standard deviation of the time series

# Output

  * `x::Vector`: time series with long memory

# Notes

Multiple dispatch is used for generation: If `d` is an integer, the function returns a time series with first or null difference. See `fracdiff` for details.

# Examples

```julia-repl
julia> fi(100,0.4)
```
