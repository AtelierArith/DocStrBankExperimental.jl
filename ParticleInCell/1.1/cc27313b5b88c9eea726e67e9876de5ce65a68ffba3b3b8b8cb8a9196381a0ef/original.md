Parent type for all grid objects, which are used to define the simulation domain, and to convert between coordinate systems. There are three different numbering systems that can refer to a location in the simulation domain:

1. The 'physical coordinates' of a point are the real (dimensionalful) coordinates associated with that point. This value can range from the lower bounds to the upper bounds of the simulation. This value will typically take the form `Vector{T}` or `NTuple{N, T}` where `T <: Real`.
2. The 'cell coordinates' of a point is the non-dimensional location of the point in units of cell lengths. This value can range from 0 to num_cells - 1, or outside this range if guard cells are included. The value will typically have the type `NTuple{N, Int}` or `NTuple{N, T}` with `T <: Real`.
3. The 'cell index' of a point is the `CartesianIndex` that can be used to index into field arrays at that point. This value must strictly be confined to `axes(field.values)`, which, for any given dimension, will typically range from 1 to num*cells + 2*num*guard_cells + 1.

The first two types of indexing, phys*coords and cell*coords, are independent of the number of guard cells in a given field, and depend only on grid quantities. Thus utilities for converting between these systems require only a reference to a grid object. On the other hand, the utilities for cell_index are specific the field being used, and thus those must be provided an `AbstractField` to do the coordinate conversion.

In general, physical coordinates are useful when considering the location of a particle, while the cell index is used to interpolate to and from the particle locations. The cell coordinates are useful for some interpolation algorithms, especially those that are defined for non-uniform grids.
