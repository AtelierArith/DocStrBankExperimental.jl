```
AbstractCoordinateSet{N}
```

An abstract type representing a set of coordinates with `N` elements.

Subtypes of `AbstractCoordinateSet` used to define specific coordinate systems or layouts used to describe physical processes, such as phase-space parametrizations for scattering events. The parameter `N` specifies the number of coordinates in the set, where `N` can be one for univariate coordinates (e.g., energy, rapidity) or higher for more complex systems.

# Type Parameters

  * `N`: The number of coordinates in the set.

# Intended Usage

Subtypes of `AbstractCoordinateSet{N}` implement the structure and behavior for specific coordinate systems. Functions like `coordinate_names` and `coordinate_name` are used to retrieve human-readable names for the coordinates in the set.
