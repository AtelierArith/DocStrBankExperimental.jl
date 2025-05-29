```
vb!(process::DiscreteHawkesProcess, data; kwargs...)
```

Perform mean-field variational inference.

The variational distribution takes the form q(λ0)q(θ)q(W)q(A)q(ω), where:

  * q(λ0) = Gamma(α, β)
  * q(θ) = Dir(γ)
  * q(W) = Gamma(kappa , ν)
  * q(A) = Bern(ρ)
  * q(ω) = Mult(u)

# Arguments

  * 
  * 

# Keyword Arguments

  * `max_steps::Int64`: maximum number of updates to perform.
  * `Δx_thresh::Float64`: ?
  * `Δq_thresh::Float64`: ?

# Return

  * `res::`: a struct containing results of the inference routine
