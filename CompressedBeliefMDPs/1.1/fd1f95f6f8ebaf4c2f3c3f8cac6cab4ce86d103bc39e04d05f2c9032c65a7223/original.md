```
CompressedBeliefMDP{B, A}
```

The `CompressedBeliefMDP` struct is a generalization of the compressed belief-state MDP presented in  [Exponential Family PCA for Belief Compression in POMDPs](https://papers.nips.cc/paper_files/paper/2002/hash/a11f9e533f28593768ebf87075ab34f2-Abstract.html).

## Type Parameters

  * `B`: The type of compressed belief states.
  * `A`: The type of actions.

## Fields

  * `bmdp::GenerativeBeliefMDP`: The generative belief-state MDP.
  * `compressor::Compressor`: The compressor used to compress belief states.
  * `ϕ::Bijection`: A bijection representing the mapping from uncompressed belief states to compressed belief states. See notes.

## Constructors

```
CompressedBeliefMDP(pomdp::POMDP, updater::Updater, compressor::Compressor)
CompressedBeliefMDP(pomdp::POMDP, sampler::Sampler, updater::Updater, compressor::Compressor)
```

Constructs a `CompressedBeliefMDP` using the specified POMDP, updater, and compressor.

!!! warning
    The 4-argument constructor is a quality-of-life constructor that calls [`fit!`](@ref) on the given compressor.


## Example Usage

```julia
pomdp = TigerPOMDP()
updater = DiscreteUpdater(pomdp)
compressor = PCACompressor(1)
mdp = CompressedBeliefMDP(pomdp, updater, compressor)
```

For continuous POMDPs, see [ParticleFilters.jl](https://juliapomdp.github.io/ParticleFilters.jl/latest/basic/).

## Notes

  * While compressions aren't usually injective, we cache beliefs and their compressions on a first-come, first-served basis, so we can effectively use a bijection without loss of generality.
