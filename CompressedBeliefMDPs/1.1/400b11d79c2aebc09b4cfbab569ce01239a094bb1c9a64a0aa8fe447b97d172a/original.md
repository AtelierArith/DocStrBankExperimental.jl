```
ExplorationPolicySampler
```

Samples belief states by rolling out an `ExplorationPolicy`. Essentially identical to `PolicySampler`.

## Fields

  * `explorer::ExplorationPolicy`: The `ExplorationPolicy` used for decision making.
  * `on_policy::Policy`: The fallback `Policy` used for decision making when not exploring.
  * `updater::Updater`: The updater used for updating beliefs.
  * `n::Integer`: The maximum number of simulated steps.
  * `rng::AbstractRNG`: The random number generator used for sampling.
  * `verbose::Bool`: Whether to use a progress bar while sampling.

## Constructors

```
ExplorationPolicySampler(pomdp::POMDP; rng::AbstractRNG=Random.GLOBAL_RNG,
explorer::ExplorationPolicy=EpsGreedyPolicy(pomdp, 0.1; rng=rng), on_policy=RandomPolicy(pomdp),
updater::Updater=DiscreteUpdater(pomdp), n::Integer=10)
```

## Methods

```
(s::ExplorationPolicySampler)(pomdp::POMDP)
```

Returns a vector of *unique* belief states.

## Example Usage

```julia-repl
julia> pomdp = TigerPOMDP()
julia> sampler = ExplorationPolicySampler(pomdp; n=30)
julia> sampler(pomdp)
3-element Vector{Any}:
 DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.5, 0.5])
 DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.85, 0.15000000000000002])
 DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.9697986577181208, 0.030201342281879207])
```
