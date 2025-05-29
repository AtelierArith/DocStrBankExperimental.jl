```
RolloutSimulator(rng, max_steps)
RolloutSimulator(; <keyword arguments>)
```

A fast simulator that just returns the reward

The simulation will be terminated when either

1. a terminal state is reached (as determined by `isterminal()` or
2. the discount factor is as small as `eps` or
3. max_steps have been executed

# Keyword arguments:

  * rng::AbstractRNG (default: Random.default_rng()) - A random number generator to use.
  * eps::Float64 (default: 0.0) - A small number; if γᵗ where γ is the discount factor and t is the time step becomes smaller than this, the simulation will be terminated.
  * max_steps::Int (default: typemax(Int)) - The maximum number of steps to simulate.

# Usage (optional arguments in brackets):

```
ro = RolloutSimulator()
history = simulate(ro, pomdp, policy, [updater [, init_belief [, init_state]]])
```

See also: [`HistoryRecorder`](@ref), [`run_parallel`](@ref)
