```
StructuredMesh(cells_per_dimension, coordinates_min, coordinates_max;
               periodicity = true)
```

Create a StructuredMesh that represents a uncurved structured mesh with a rectangular domain.

# Arguments

  * `cells_per_dimension::NTuple{NDIMS, Int}`: the number of cells in each dimension.
  * `coordinates_min::NTuple{NDIMS, RealT}`: coordinate of the corner in the negative direction of each dimension.
  * `coordinates_max::NTuple{NDIMS, RealT}`: coordinate of the corner in the positive direction of each dimension.
  * `periodicity`: either a `Bool` deciding if all of the boundaries are periodic or an `NTuple{NDIMS, Bool}` deciding for                each dimension if the boundaries in this dimension are periodic.
