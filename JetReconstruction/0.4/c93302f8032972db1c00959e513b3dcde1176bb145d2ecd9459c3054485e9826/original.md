```
constituents(jet::T, cs::ClusterSequence{T}) where T <: FourMomentum
```

Get the constituents of a given jet in a cluster sequence.

# Arguments

  * `cs::ClusterSequence{T}`: The cluster sequence object.
  * `jet::T`: The jet for which to retrieve the constituents.

# Returns

An array of jet objects (which are of the same type as the input jet) representing the constituents of the given jet,  
