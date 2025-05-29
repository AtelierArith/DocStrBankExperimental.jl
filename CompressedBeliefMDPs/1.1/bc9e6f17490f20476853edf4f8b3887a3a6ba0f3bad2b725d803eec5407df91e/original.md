```
BeliefExpansionSampler
```

Fast extension of exploratory belief expansion (Algorithm 21.13 in [Algorithms for Decision Making](https://algorithmsbook.com/)) that uses $k$-d trees.

## Fields

  * `updater::Updater`: The updater used to update beliefs.
  * `metric::NearestNeighbors.MinkowskiMetric`: The metric used to measure distances between beliefs.

It must be a [Minkowski metric](https://en.wikipedia.org/wiki/Minkowski_distance).

  * `n::Integer`: The number of belief expansions to perform.

## Constructors

```
BeliefExpansionSampler(pomdp::POMDP; updater::Updater=DiscreteUpdater(pomdp),
metric::NearestNeighbors.MinkowskiMetric=Euclidean(), n::Integer=3)
```

## Methods

```
(s::BeliefExpansionSampler)(pomdp::POMDP)
```

Creates an initial belief and performs exploratory belief expansion. Returns the unique belief states.  Only works for POMDPs with discrete state, action, and observation spaces.

## Example Usage

```julia-repl
julia> pomdp = TigerPOMDP();
julia> sampler = BeliefExpansionSampler(pomdp; n=2);
julia> beliefs = sampler(pomdp)
Set{DiscreteBelief{TigerPOMDP, Bool}} with 4 elements:
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.15000000000000002, 0.85])
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.5, 0.5])
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.85, 0.15000000000000002])
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.9697986577181208, 0.030201342281879207])
```
