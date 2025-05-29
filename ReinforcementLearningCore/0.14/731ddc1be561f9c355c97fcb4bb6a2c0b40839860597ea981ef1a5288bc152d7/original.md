```
EpsilonGreedyExplorer{T}(;kwargs...)
EpsilonGreedyExplorer(ϵ) -> EpsilonGreedyExplorer{:linear}(; ϵ_stable = ϵ)
```

> Epsilon-greedy strategy: The best lever is selected for a proportion `1 - epsilon` of the trials, and a lever is selected at random (with uniform probability) for a proportion epsilon . [Multi-armed_bandit](https://en.wikipedia.org/wiki/Multi-armed_bandit)


Two kinds of epsilon-decreasing strategy are implemented here (`linear` and `exp`).

> Epsilon-decreasing strategy: Similar to the epsilon-greedy strategy, except that the value of epsilon decreases as the experiment progresses, resulting in highly explorative behaviour at the start and highly exploitative behaviour at the finish.  - [Multi-armed_bandit](https://en.wikipedia.org/wiki/Multi-armed_bandit)


# Keywords

  * `T::Symbol`: defines how to calculate the epsilon in the warmup steps. Supported values are `linear` and `exp`.
  * `step::Int = 1`: record the current step.
  * `ϵ_init::Float64 = 1.0`: initial epsilon.
  * `warmup_steps::Int=0`: the number of steps to use `ϵ_init`.
  * `decay_steps::Int=0`: the number of steps for epsilon to decay from `ϵ_init` to `ϵ_stable`.
  * `ϵ_stable::Float64`: the epsilon after `warmup_steps + decay_steps`.
  * `is_break_tie=false`: randomly select an action of the same maximum values if set to `true`.
  * `rng=Random.default_rng()`: set the internal RNG.

# Example

```julia
s_lin = EpsilonGreedyExplorer(kind=:linear, ϵ_init=0.9, ϵ_stable=0.1, warmup_steps=100, decay_steps=100)
plot([RLCore.get_ϵ(s_lin, i) for i in 1:500], label="linear epsilon")
s_exp = EpsilonGreedyExplorer(kind=:exp, ϵ_init=0.9, ϵ_stable=0.1, warmup_steps=100, decay_steps=100)
plot!([RLCore.get_ϵ(s_exp, i) for i in 1:500], label="exp epsilon")
```

![](https://github.com/JuliaReinforcementLearning/ReinforcementLearning.jl/raw/main/docs/src/assets/epsilon_greedy_selector.png)
