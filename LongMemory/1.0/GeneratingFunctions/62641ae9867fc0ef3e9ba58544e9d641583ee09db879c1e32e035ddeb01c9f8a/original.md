```
hwp_gen(T;μ=0,σ=1)
```

Generate a time series with long memory using the harmonically weighted process à la Hassler and Hosseinkouchack (2020).

# Arguments

  * `T::Int`: length of the time series
  * `μ::Float64`: mean of the time series
  * `σ::Float64`: standard deviation of the time series

# Output

  * `x::Vector`: time series with long memory

# Examples

```julia-repl
julia> hwp_gen(100)
```
