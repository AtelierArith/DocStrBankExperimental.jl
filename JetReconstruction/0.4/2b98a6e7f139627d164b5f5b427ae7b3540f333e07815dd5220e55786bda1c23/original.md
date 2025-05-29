```
exclusive_jets(clusterseq::ClusterSequence{U}; dcut = nothing, njets = nothing, T = LorentzVectorCyl) where {U}
```

Return all exclusive jets of a ClusterSequence, with either a specific number of jets or a cut on the maximum distance parameter.

# Arguments

  * `clusterseq::ClusterSequence`: The `ClusterSequence` object containing the clustering history and jets.
  * `dcut::Union{Nothing, Real}`: The distance parameter used to define the exclusive jets. If `dcut` is provided, the number of exclusive jets will be calculated based on this parameter.
  * `njets::Union{Nothing, Integer}`: The number of exclusive jets to be calculated. If `njets` is provided, the distance parameter `dcut` will be calculated based on this number.
  * `T = LorentzVectorCyl`: The return type used for the selected jets.

**Note**: Either `dcut` or `njets` must be provided (but not both).

# Returns

  * An array of `T` objects representing the exclusive jets.

Valid return types are `LorentzVectorCyl` and the jet type of the input `clusterseq` (`U` - either `PseudoJet` or `EEjet` depending which algorithm was used) (N.B. this will evolve in the future to be any subtype of `FourMomentumBase`; currently unrecognised types will return `LorentzVectorCyl`).

# Exceptions

  * `ArgumentError`: If neither `dcut` nor `njets` is provided.
  * `ArgumentError`: If the algorithm used in the `ClusterSequence` object is not suitable for exclusive jets.
  * `ErrorException`: If the cluster sequence is incomplete and exclusive jets are unavailable.

# Examples

```julia
exclusive_jets(clusterseq, dcut = 20.0)
exclusive_jets(clusterseq, njets = 3, T = PseudoJet)
```
