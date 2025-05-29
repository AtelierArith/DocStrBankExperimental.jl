```
coordinate_names(coord_set::AbstractCoordinateSet)
```

Retrieve the names of all coordinates in a given coordinate set.

# Arguments

  * `coord_set::AbstractCoordinateSet`: A coordinate set, which is a container for multiple

coordinates.

# Returns

  * A tuple of strings, where each string is the name of a coordinate in the set, including its particle index if available.

This function is typically implemented for subtypes of `AbstractCoordinateSet` and is used to return human-readable names for each coordinate in the set.
