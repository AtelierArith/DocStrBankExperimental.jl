```
CoordinateSet{N, D<:Tuple}
```

A concrete type that represents a set of `N` coordinates, stored as a tuple `coords::D`. This type is a subtype of `AbstractCoordinateSet{N}` and is designed to handle sets of coordinates for use in various calculations, such as in phase space layouts.

# Fields

  * `coords::D`: A tuple containing the individual coordinates. Each element of the tuple   corresponds to a coordinate in the set.

# Constructors

  * `CoordinateSet{N}(coords::D)`: Creates a `CoordinateSet` where the number of coordinates   `N` must match the length of the tuple `coords`. If they do not match,   an `ArgumentError` is thrown.
  * `CoordinateSet(coords::D)`: Automatically infers `N` as the length of the provided tuple   `coords`.

# Throws

  * `ArgumentError` if the length of the provided tuple does not match the specified   number `N`.
