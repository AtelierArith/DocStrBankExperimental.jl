```
initialize_state_draws(s0::Vector{Float64}, F_ϵ::Distribution, Φ::Function,
                       n_parts::Int; burn::Int = 10000, thin::Int = 5)
```

### Inputs

  * `s0::Vector`: An initial guess/starting point to begin iterating the   states forward.
  * `F_ϵ::Distribution`: The shock distribution: ϵ ~ F_ϵ
  * `Φ::Function`: The state transition function: s*t = Φ(s*t-1, ϵ_t)
  * `n_parts::Int`: The number of particles (draws) to generate

### Keyword Arguments

  * `initialize::Bool`: Flag indicating whether one is solving for incremental   weights during the initialization of weights; default is `false`.
  * `burn::Int`: The number of draws to burn in before the draws are actually   collected. This is under the assumption that the s_t reaches its stationary   distribution post burn-in.
  * `thin::Int`: The number of draws to thin by to minimize serial correlation

### Output

  * `s_init`: A matrix (# of states x # of particles) containing the initial   draws of states to start

the tpf algorithm from.
