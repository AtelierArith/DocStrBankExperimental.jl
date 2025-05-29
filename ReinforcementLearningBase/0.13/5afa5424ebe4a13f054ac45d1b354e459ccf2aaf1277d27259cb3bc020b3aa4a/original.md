```
plan!(π::AbstractPolicy, env) -> action
```

The policy is the most basic concept in reinforcement learning. Here an agent's action is determined by a `plan!` which takes an environment and policy and returns an action.

!!! note
    See discussions [here](https://github.com/JuliaReinforcementLearning/ReinforcementLearning.jl/issues/86) if you are wondering why we define the input as `AbstractEnv` instead of state.


!!! warning
    The policy `π` may change its internal state but it shouldn't change `env`. When it's really necessary, remember to make a copy of `env` to keep the original `env` untouched.

