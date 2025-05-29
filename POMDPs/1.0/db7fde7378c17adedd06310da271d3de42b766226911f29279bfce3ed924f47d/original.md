```
gen(m::Union{MDP,POMDP}, s, a, rng::AbstractRNG)
```

Function for implementing the entire MDP/POMDP generative model by returning a `NamedTuple`.

`gen` should *only* be implemented in the case where *two or more* of the next state, observation, and reward need to be generated at the same time. If the state transition model can be separated from the reward and observation models, you should implement `transition` with an `ImplicitDistribution` instead of `gen`.

Solver and simulator writers should use the `@gen` macro to call a generative model.

# Arguments

  * `m`: an `MDP` or `POMDP` model
  * `s`: the current state
  * `a`: the action
  * `rng`: a random number generator (Typically a `MersenneTwister`)

# Return

The function should return a [`NamedTuple`](https://docs.julialang.org/en/v1/base/base/#Core.NamedTuple). With a subset of following entries:

## MDP

  * `sp`: the next state
  * `r`: the reward for the step
  * `info`: extra debugging information, typically in an associative container like a NamedTuple

## POMDP

  * `sp`: the next state
  * `o`: the observation
  * `r`: the reward for the step
  * `info`: extra debugging information, typically in an associative container like a NamedTuple

Some elements can be left out. For instance if `o` is left out of the return, the problem-writer can also implement `observation` and POMDPs.jl will automatically use it when needed.

# Example

```julia
struct LQRMDP <: MDP{Float64, Float64} end

POMDPs.gen(m::LQRMDP, s, a, rng) = (sp = s + a + randn(rng), r = -s^2 - a^2)
```
