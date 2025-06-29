```
MatchBySSSetDistance(; distance = Centroid(), threshold = Inf, use_vanished = false)
```

A matcher type that matches IDs by the distance of their corresponding state space sets.

## Keyword arguments

  * `distance = Centroid()`: distance to match by, given to [`setsofsets_distances`](@ref).
  * `threshold = Inf`: sets with distance larger than the `threshold` are guaranteed to not be mapped to each other.
  * `use_vanished = !isinf(threshold)`: value of the keyword `use_vanished` when used in [`match_sequentially!`](@ref).

## Description

In this matcher the values compared are [`StateSpaceSet`](@ref)s which in most cases represent attractors in the state space, but may also represent any other set such as a group of features.

Here is how this matcher works: (recall in this conversation that sets/attractors are stored in dictionaries, mapping keys/IDs to the sets, and we want to match keys in the "new" dictionary (`a₊`) to those in the "old" dictionary (`a₋`)).

The distance between all possible pairs of sets between the "old" sets and "new" sets is computed as a formal distance between sets. This is controlled by the `distance` option, itself given to the lower-level [`setsofsets_distances`](@ref) function, so `distance` can be whatever that function accepts. That is, one of [`Centroid`](@ref), [`Hausdorff`](@ref), [`StrictlyMinimumDistance`](@ref), or any arbitrary user-provided function `f` that given two sets `f(A, B)` it returns a positive number (their distance).

Sets (in particular, their corresponding IDs) are then matched according to this distance. First, all possible ID pairs (old, new) are sorted according to the distance of their corresponding sets. The pair with smallest distance is matched. IDs in matched pairs are removed from the matching pool to ensure a unique mapping. Then, the next pair with least remaining distance is matched, and the process repeats until all pairs are exhausted.

Additionally, you can provide a `threshold` value. If the distance between two sets is larger than this `threshold`, then it is guaranteed that the two sets will get assigned different ID in the replacement map, and hence, the set in `a₊` gets the next available integer as its ID.
