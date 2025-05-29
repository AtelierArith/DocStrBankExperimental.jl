```
parent_jets(jet::T, cs::ClusterSequence{T})::Tuple{Union{Nothing, T}, Union{Nothing, T}} where {T <: FourMomentum}
```

Find the parent jets of a given jet in a cluster sequence.

# Arguments

  * `jet::T`: The jet for which to find the parent jets.
  * `cs::ClusterSequence`: The cluster sequence object.

# Returns

A tuple of two elements, each of which is either the parent jet object or `nothing` (if the jet has no parent).
