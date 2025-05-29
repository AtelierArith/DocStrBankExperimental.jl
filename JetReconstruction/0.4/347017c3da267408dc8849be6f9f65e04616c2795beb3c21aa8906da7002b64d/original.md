```
constituent_indexes(jet::T, cs::ClusterSequence{T}) where T <: FourMomentum
```

Return the indexes of the original particles which are the constituents of the given jet.

# Arguments

  * `jet::T`: The jet for which to retrieve the constituents.
  * `cs::ClusterSequence{T}`: The cluster sequence object.

# Returns

An vector of indices representing the original constituents of the given jet.
