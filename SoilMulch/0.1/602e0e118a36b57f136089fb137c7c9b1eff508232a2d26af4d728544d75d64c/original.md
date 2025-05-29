`rainfall_poisson(n, α, λ)`

Generates rainfall using Poisson process.

# Arguments

  * `n::Integer`: number of events.
  * `α::Float64`: mean rain depth.
  * `λ::Float64`: rain event interval (1/d).

If rainfall needs to be similated in timescale smaller than daily, multiply `λ` by dt.

# Example

```
n = 30
α = 0.75
λ = 0.45
rain = rainfall_poisson(n, α, λ)
```
