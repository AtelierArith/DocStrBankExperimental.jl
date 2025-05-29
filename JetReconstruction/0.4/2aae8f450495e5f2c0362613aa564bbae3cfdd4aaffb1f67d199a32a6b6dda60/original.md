```
tiled_jet_reconstruct(particles::AbstractVector{T}; p::Union{Real, Nothing} = -1,
                           algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing,
                           R = 1.0, recombine = +) where {T}
```

Main jet reconstruction algorithm entry point for reconstructing jets using the tiled strategy for generic jet type T.

**Note** - if a non-standard recombination is used, it must be defined for JetReconstruction.PseudoJet, as this struct is used internally.

This code will use the `k_t` algorithm types, operating in `(rapidity, φ)` space.

It is not necessary to specify both the `algorithm` and the `p` (power) value. If both are given they must be consistent or an exception is thrown.

## Arguments

  * `particles::AbstractVector{T}`: A vector of particles used as input for jet reconstruction. T must support methods px, py, pz and energy (defined in the JetReconstruction namespace)
  * `p::Union{Real, Nothing} = -1`: The power parameter for the jet reconstruction algorithm, thus switching between different algorithms.
  * `algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing`: The explicit jet algorithm to use.
  * `R::Float64 = 1.0`: The jet radius parameter for the jet reconstruction algorithm.
  * `recombine::Function = +`: The recombination function used for combining pseudojets.

## Returns

  * `Vector{PseudoJet}`: A vector of reconstructed jets.

## Example

```julia
tiled_jet_reconstruct(particles::Vector{LorentzVectorHEP}; p = -1, R = 0.4, recombine = +)
```
