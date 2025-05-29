```
iterative_boltzmann(pot::Function, dim::Int, ρ::Float64, targ_g2::Function, α = 1; n = 500, bin_size = 0.05, r_range = 10)::Function
```

Iteratively updates the pair potential `pot` using the Boltzmann inversion method to match the target pair correlation function `targ_g2`.

# Arguments

  * `pot::Function`: The initial pair potential function to be optimized.
  * `dim::Int`: The dimensionality of the system.
  * `ρ::Float64`: The number density of particles in the system.
  * `targ_g2::Function`: The target pair correlation function $g_2(r)$.
  * `α::Float64`: The update parameter for the potential. (Optional, default: 1)

# Keyword Arguments (All are optional)

  * `n`: Number of particles for each box in the simulation. (default: 500)
  * `bin_size`: Bin size for the histograms of pair correlation functions. (default: 0.05)
  * `r_range`: Maximum distance to compute the pair correlation function. (default: 10)
  * `n_threads`: Number of threads to use for parallel computation. (default: 15)
  * `configs_per_thread`: Number of configurations to generate for each thread. (default: 10)
  * `displace`: Kick size in the metropolis Monte Carlo simulation. (default: 0.2).
  * `Ψ_tol`: Tolerance of the distance metric between the target and simulated $g_2$ for stopping criterion. (default: 0.005)
  * `show_pb`: Whether to show the progress bar during the simulation. (default: true)
  * `test`: Whether to run the function in test mode. (default: false)

# Returns

  * If `test=true`, returns a boolean indicating whether the optimization is successful.
  * Otherwise, returns the optimized pair potential function.

# Example

```
optimized_potential = iterative_boltzmann(r -> 0, 2, 1.0, r -> 1 - exp(-π*r^2))
```
