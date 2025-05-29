```
StructuredMesh(cells_per_dimension, mapping;
               RealT = Float64,
               periodicity = true,
               unsaved_changes = true, 
               mapping_as_string = mapping2string(mapping, length(cells_per_dimension), RealT=RealT))
```

Create a StructuredMesh of the given size and shape that uses `RealT` as coordinate type.

# Arguments

  * `cells_per_dimension::NTupleE{NDIMS, Int}`: the number of cells in each dimension.
  * `mapping`: a function of `NDIMS` variables to describe the mapping, which transforms            the reference mesh to the physical domain.            If no `mapping_as_string` is defined, this function must be defined with the name `mapping`            to allow for restarts.            This will be changed in the future, see [https://github.com/trixi-framework/Trixi.jl/issues/541](https://github.com/trixi-framework/Trixi.jl/issues/541).
  * `RealT::Type`: the type that should be used for coordinates.
  * `periodicity`: either a `Bool` deciding if all of the boundaries are periodic or an `NTuple{NDIMS, Bool}`                deciding for each dimension if the boundaries in this dimension are periodic.
  * `unsaved_changes::Bool`: if set to `true`, the mesh will be saved to a mesh file.
  * `mapping_as_string::String`: the code that defines the `mapping`.                              If `CodeTracking` can't find the function definition, it can be passed directly here.                              The code string must define the mapping function with the name `mapping`.                              This will be changed in the future, see [https://github.com/trixi-framework/Trixi.jl/issues/541](https://github.com/trixi-framework/Trixi.jl/issues/541).
