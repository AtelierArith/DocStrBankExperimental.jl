```
sir(
    β = 0.5, γ = 0.25, N = 10000,
    ρ = 0.3, k = 10,
    S₀ = 0.9, I₀ = 0.01, R₀ = 0.1,
    δt = 0.1, t₀ = 0.0,
    times = range(start=1.0,stop=90,step=1.0)
   )
```

`sir` returns a *PompObject* containing simulated SIR data.

## Parameters

  * β: transmission rate
  * γ: recovery rate
  * N: population size
  * ρ: reporting rate
  * k: overdispersion coefficient (negative binomial size parameter)
  * S₀, I₀, R₀: relative proportions of susceptible, infected, recovered (respectively) in the population at t=t₀.
  * δt: Euler stepsize
  * t₀: zero-time
  * times: vector of observation times
