```
Street
```

Store an edge between two [`Junction`](@ref)s.

# Fields

  * `endpointA::Int`: index of the first junction
  * `endpointB::Int`: index of the second junction
  * `bidirectional::Bool`: whether `B -> A` is allowed
  * `duration::Int`: time cost of traversing the street (in seconds)
  * `distance::Int`: length of the street (in meters)
