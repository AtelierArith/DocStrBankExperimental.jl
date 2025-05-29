```
salp(N::T; θ::Float64=1.0, steps::Int64=10_000, λ::Float64=0.999, progress::Bool=false) where {T <: BipartiteNetwork}
```

Label-propagation using simulated annealing. This function uses simulated annealing to propagate labels from neighboring nodes. It accepts a network as input. The schedule of the simulated annealing is linear: at step k+1, the temperature is θλᵏ. The initial temperature has been picked so that after 100 timesteps, using the default λ, a move decreasing modularity by 0.05 (20% of the theoretical maximum) is picked with a probability of 0.1.

Optional arguments regulating the behavior of the simulated annealing routine are:

  * `λ=0.999`, the rate of temperature decay
  * `θ=0.002`, the initial temperature
  * `steps=10_000`, the number of annealing steps to perform
  * `progress=false`, whether to display an info message every 100 timesteps

The θ parameter can be picked using the following method: if we want to allow a maximal loss of modularity of δ, after timestep k, with a decay parameter λ, with a probability P, then θ = -δ/[λᵏ×ln(P)]⁻¹. By beibg more or less restrictive on these parameters, the user can pick a value of θ for every problem.

This function can work as a first step (like `lp`), but in explorations during the development of the package, we found that `brim` was rarely (if ever) able to optmize the output further. It can therefore be used on its own.
