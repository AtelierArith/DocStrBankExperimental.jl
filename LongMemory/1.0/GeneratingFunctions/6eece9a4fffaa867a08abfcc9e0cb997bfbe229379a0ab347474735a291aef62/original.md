```
arfi_gen(T::Int, μ::Real, AR::Array, d::Real; σ=1)
```

Generate a time series with long memory parameter `d` and length `T` using the ARFIMA(p,d,0) model.

# Arguments

  * `T::Int`: length of the time series
  * `μ::Float64`: mean of the time series
  * `AR::Array`: AR coefficients
  * `d::Float64`: fractional difference parameter

# Optional arguments

  * `σ::Float64`: standard deviation of the time series

# Output

  * `x::Vector`: time series with long memory

# Notes

The code is inspired by the function `dgp_arfima.m` by [Carlos Vladimir Rodríguez Caballero (2023)](https://www.mathworks.com/matlabcentral/fileexchange/53301-arfima-p-d-q)

# Examples

```julia-repl
julia> arfi_gen(100, 0, [0.2; -0.5], 0.4])
```
