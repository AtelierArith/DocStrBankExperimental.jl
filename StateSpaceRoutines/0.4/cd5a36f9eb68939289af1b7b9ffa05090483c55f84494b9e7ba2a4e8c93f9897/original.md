```
tempered_particle_filter(data, Φ, Ψ, F_ϵ, F_u, s_init; verbose = :high,
    n_particles = 1000, fixed_sched = [], r_star = 2, findroot = bisection,
    xtol = 1e-3, resampling_method = :multionial, n_mh_steps = 1, c_init = 0.3,
    target_accept_rate = 0.4, n_presample_periods = 0, allout = true,
    parallel = false, verbose = :low,
    dynamic_measurement = false, poolmodel = false)
```

### Inputs

  * `data::Matrix{S}`: `Ny` x `Nt` matrix of historical data
  * `Φ::Function`: state transition equation: s*t = Φ(s*{t-1}, ϵ_t)
  * `Ψ::Function`: measurement equation: y*t = Ψ(s*t) + u_t
  * `F_ϵ::Distribution`: shock distribution: ϵ*t ~ F*ϵ
  * `F_u::Distribution`: measurement error distribution: u*t ~ F*u
  * `s_init::Matrix{S}`: `Ns` x `n_particles` matrix of initial state vectors s_0

where `S<:AbstractFloat` and

  * `Ns` is the number of states
  * `Ny` is the number of observables
  * `Nt` is the number of data periods

### Keyword Arguments

  * `n_particles::Int`: number of particles used to approximate the log-likelihood. Using more particles yields a more accurate estimate, at the cost of being more computationally intensive

**Correction:**

  * `fixed_sched::Vector{S}`: array of monotone increasing values in (0,1] which specify the fixed tempering schedule. Set to `[]` if you wish to adaptively choose the tempering schedule (below)
  * `r_star::S`: target inefficiency ratio used to adaptively choose φ, i.e. Ineff(φ*n) := 1/M Σ*{j=1}^M (Wtil*t^{j,n}(φ*n))^2 = r_star
  * `findroot::Function`: root-finding algorithm, one of `bisection` or `fzero`
  * `xtol::S`: root-finding tolerance on x bracket size

**Selection:**

  * `resampling_method::Symbol`: either `:multinomial` or `:systematic`

**Mutation:**

  * `n_mh_steps::Int`: number of Metropolis-Hastings steps to take in each tempering stage
  * `c_init::S`: initial scaling of proposal covariance matrix
  * `target_accept_rate::S`: target Metropolis-Hastings acceptance rate

**Other:**

  * `n_presample_periods::Int`: number of initial periods to omit from the log-likelihood calculation
  * `allout::Bool`: whether to return all outputs or just `sum(loglh)`
  * `parallel::Bool`: whether to use `DistributedArray`s
  * `verbose::Symbol`: amount to print to STDOUT. One of `:none`, `:low`, or `:high`

### Outputs

  * `sum(loglh)::S`: log-likelihood p(y*{1:T}|Φ,Ψ,F*ϵ,F_u) approximation
  * `loglh::Vector{S}`: vector of conditional log-likelihoods p(y*t|y*{1:t-1},Φ,Ψ,F*ϵ,F*u)
  * `times::Vector{S}`: vector of runtimes per period t
