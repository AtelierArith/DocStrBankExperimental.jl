```
StructuredMesh(cells_per_dimension, faces; 
               RealT = Float64,
               periodicity = true)
```

Create a StructuredMesh of the given size and shape that uses `RealT` as coordinate type.

# Arguments

  * `cells_per_dimension::NTupleE{NDIMS, Int}`: the number of cells in each dimension.
  * `faces::NTuple{2*NDIMS}`: a tuple of `2 * NDIMS` functions that describe the faces of the domain.                           Each function must take `NDIMS-1` arguments.                           `faces[1]` describes the face onto which the face in negative x-direction                           of the unit hypercube is mapped. The face in positive x-direction of                           the unit hypercube will be mapped onto the face described by `faces[2]`.                           `faces[3:4]` describe the faces in positive and negative y-direction respectively                           (in 2D and 3D).                           `faces[5:6]` describe the faces in positive and negative z-direction respectively (in 3D).
  * `RealT::Type`: the type that should be used for coordinates.
  * `periodicity`: either a `Bool` deciding if all of the boundaries are periodic or an `NTuple{NDIMS, Bool}` deciding for                each dimension if the boundaries in this dimension are periodic.
