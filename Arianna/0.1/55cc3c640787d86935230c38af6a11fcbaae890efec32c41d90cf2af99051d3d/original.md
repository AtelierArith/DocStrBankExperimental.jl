```
mc_step!(system::AriannaSystem, action::Action, policy::Policy, parameters::AbstractArray{T}, rng) where {T<:AbstractFloat}
```

Perform a single Monte Carlo step.

# Arguments

  * `system`: System to modify
  * `action`: Action to perform
  * `policy`: Policy used for proposal
  * `parameters`: Parameters of the policy
  * `rng`: Random number generator
