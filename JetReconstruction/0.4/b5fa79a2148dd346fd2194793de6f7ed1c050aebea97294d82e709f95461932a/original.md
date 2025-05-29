```
plain_jet_reconstruct(particles::AbstractVector{T}; p::Union{Real, Nothing} = -1,
                           algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing,
                           R = 1.0, recombine = +) where {T}
```

Perform pp jet reconstruction using the plain algorithm.

# Arguments

  * `particles::AbstractVector{T}`: A vector of particles used for jet  reconstruction, any array of particles, which supports suitable 4-vector  methods, viz. pt2(), phi(), rapidity(), px(), py(), pz(), energy(), can be  used. for each element.
  * `p::Union{Real, Nothing} = -1`: The power value used for jet reconstruction.
  * `algorithm::Union{JetAlgorithm, Nothing} = nothing`: The explicit jet algorithm to use.
  * `R::Float64 = 1.0`: The radius parameter used for jet reconstruction.
  * `recombine::Function = +`: The recombination function used for jet reconstruction.

**Note** for the `particles` argument, the 4-vector methods need to exist in the JetReconstruction package namespace.

This code will use the `k_t` algorithm types, operating in `(rapidity, φ)` space.

It is not necessary to specify both the `algorithm` and the `p` (power) value. If both are given they must be consistent or an exception is thrown.

# Returns

  * `Vector{PseudoJet}`: A vector of reconstructed jets.

# Example

```julia
jets = plain_jet_reconstruct(particles; p = -1, R = 0.4)
jets = plain_jet_reconstruct(particles; algorithm = JetAlgorithm.Kt, R = 1.0)
```
