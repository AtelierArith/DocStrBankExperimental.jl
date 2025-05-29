```
PolicySampler
```

Samples belief states by rolling out a `Policy`.

## Fields

  * `policy::Policy`: The policy used for decision making.
  * `updater::Updater`: The updater used for updating beliefs.
  * `n::Integer`: The maximum number of simulated steps.
  * `rng::AbstractRNG`: The random number generator used for sampling.
  * `verbose::Bool`: Whether to use a progress bar while sampling.

## Constructors

```
PolicySampler(pomdp::POMDP; policy::Policy=RandomPolicy(pomdp), 
updater::Updater=DiscreteUpdater(pomdp), n::Integer=10, 
rng::AbstractRNG=Random.GLOBAL_RNG)
```

## Methods

```
(s::PolicySampler)(pomdp::POMDP)
```

Returns a vector of *unique* belief states.

# Example

```julia-repl
julia> pomdp = TigerPOMDP();
julia> sampler = PolicySampler(pomdp; n=3); 
julia> 2-element Vector{Any}:
DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.5, 0.5])
DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.15000000000000002, 0.85])
```
