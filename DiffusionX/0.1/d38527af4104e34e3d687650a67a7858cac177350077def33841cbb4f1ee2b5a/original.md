```
TAMSD(TA::TimeAverage, order::Int, τ::Float64, N::Int)
𝔼(TA::TimeAverage; τ::Float64=1e-2, N::Int=100_000, order::Int=10)
```

Calculate the time average mean square displacement (TAMSD).

# Arguments

  * `TA` : The time average, constructed by the constructor `δ̄²(::StochasticProcess, T::Real, Δ::Real)`
  * `τ` : The time step of the Euler method
  * `N` : The number of particles in the Monte Carlo simulation
  * `order` : The number of terms in the Gaussian-Legendre quadrature

# Usage

```julia
T = 100; Δ = 1
x::StochasticProcess = ....  # Define a stochastic process instance
𝔼(δ̄²(x, T, Δ))  # Calculate TAMSD
```
