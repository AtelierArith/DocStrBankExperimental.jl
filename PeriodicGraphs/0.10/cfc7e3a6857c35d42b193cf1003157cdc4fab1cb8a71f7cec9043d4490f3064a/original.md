```
strong_erings([rs::Vector{Vector{Int}},], g::PeriodicGraph{D}, [depth=15,] ringsymms::AbstractSymmetryGroup=NoSymmetryGroup(length(rs))) where D
```

Compute the list of strong edge rings in `g`, up to length `2*depth+3`. See [`strong_rings`](@ref) and [`rings`](@ref) for the meaning of the optional arguments.

Return a quadruplet of values:

  * the two first values are the list of rings and their symmetry group, identical to the result of [`strong_rings`](@ref), unless `rs` is provided (see below).
  * the third is the list of edge rings: each edge of the periodic graph is mapped to an integer and each ring is represented by the sorted list of its edges.
  * the last is the mapping from edges to integers, given as an [`EdgeDict`](@ref).

If `rs` is provided, the first returned value is the list of indices `keep` of `rs` such that `rs[keep]` is the list of strong rings.
