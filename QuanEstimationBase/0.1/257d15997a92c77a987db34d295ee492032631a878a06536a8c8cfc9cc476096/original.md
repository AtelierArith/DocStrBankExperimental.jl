```
PSO(;max_episode::Union{T,Vector{T}} where {T<:Int}=[1000, 100], p_num::Number=10, ini_particle=nothing, c0::Number=1.0, c1::Number=2.0, c2::Number=2.0, seed::Number=1234)
```

Optimization algorithm: PSO.

  * `max_episode`: The number of episodes, it accepts both integer and array with two elements.
  * `p_num`: The number of particles.
  * `ini_particle`: Initial guesses of the optimization variables.
  * `c0`: The damping factor that assists convergence, also known as inertia weight.
  * `c1`: The exploitation weight that attracts the particle to its best previous position, also known as cognitive learning factor.
  * `c2`: The exploitation weight that attracts the particle to the best position in the neighborhood, also known as social learning factor.
