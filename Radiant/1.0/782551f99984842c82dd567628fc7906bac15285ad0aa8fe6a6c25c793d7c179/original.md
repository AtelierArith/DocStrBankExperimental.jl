```
Geometry
```

Structure used to define the geometry properties of the medium for transport calculations.

# Mandatory field(s)

  * `name::String` : name (or identifier) of the Geometry structure.
  * `dimension::Int64` : dimension of the geometry.
  * `material_per_region::Array{Material}` : multidimensional array of the material per regions.
  * `boundary_conditions::Dict{String,Int64}` : boundary conditions along each axis.
  * `number_of_regions::Dict{String,Int64}` : number of regions along each axis.
  * `voxels_per_region::Dict{String,Vector{Int64}}` : number of voxels inside each regions along each axis.
  * `region_boundaries::Dict{String,Vector{Float64}}` : boundaries of each regions along each axis.

# Optional field(s) - with default values

  * `type::String="cartesian"` : type of geometry.
