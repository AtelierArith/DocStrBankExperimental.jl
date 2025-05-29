```
inclusive_jets(clusterseq::ClusterSequence{U}; ptmin = 0.0, T = LorentzVectorCyl) where {U}
```

Return all inclusive jets of a ClusterSequence with pt > ptmin.

# Arguments

  * `clusterseq::ClusterSequence`: The `ClusterSequence` object containing the clustering history and jets.
  * `ptmin::Float64 = 0.0`: The minimum transverse momentum (pt) threshold for the inclusive jets.
  * `T = LorentzVectorCyl`: The return type used for the selected jets.

# Returns

An array of `T` objects representing the inclusive jets.

# Description

This function computes the inclusive jets from a given `ClusterSequence` object. It iterates over the clustering history and checks the transverse momentum of each parent jet. If the transverse momentum is greater than or equal to `ptmin`, the jet is added to the array of inclusive jets.

Valid return types are `LorentzVectorCyl` and the jet type of the input `clusterseq` (`U` - either `PseudoJet` or `EEjet` depending which algorithm was used) (N.B. this will evolve in the future to be any subtype of `FourMomentumBase`; currently unrecognised types will return `LorentzVectorCyl`).

# Example

```julia
inclusive_jets(clusterseq; ptmin = 10.0)
```
