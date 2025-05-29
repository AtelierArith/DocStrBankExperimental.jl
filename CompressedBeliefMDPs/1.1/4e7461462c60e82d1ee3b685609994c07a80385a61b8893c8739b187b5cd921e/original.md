```
compress_POMDP(pomdp, sampler, updater, compressor)
```

Creates a compressed belief-state MDP by sampling, compressing, and caching beliefs from the given POMDP.

# Arguments

  * `pomdp::POMDP`: The POMDP model to be compressed.
  * `sampler::Sampler`: A sampler to generate a set of beliefs from the POMDP.
  * `updater::Updater`: An updater to initialize beliefs from states.
  * `compressor::Compressor`: A compressor to reduce the dimensionality of the beliefs.

# Returns

  * `CompressedBeliefMDP`: The constructed compressed belief-state MDP.
  * `Matrix{Float64}`: A matrix where each row corresponds to the compressed representation of the sampled beliefs.

# Example Usage

```julia pomdp = TigerPOMDP() sampler = BeliefExpansionSampler(pomdp) updater = DiscreteUpdater(pomdp) compressor = PCACompressor(2) m, B̃ = compress_POMDP(pomdp, sampler, updater, compressor)
