# Method p47

Analysis of plates (Plane structural element) using 4-node Quadrilateral finite elements. Homogeneous material with identical elements. Mesh numbered in x or y direction.

### Constructors

```julia
p47(data)
```

### Arguments

```julia
* `data::Dict{Symbol, Any}` : Dictionary containing all input data
```

### Required data dictionary keys

```julia
* struc_el::StructuralElement                          : Structural element
* support::Array{Tuple{Int,Array{Int,1}},1}        : Fixed-displacements vector
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : Node load vector
* properties::Vector{Float64}                          : Material properties
* x_coords::FloatRange{Floalt64}                       : x-coordinate vector
* y_coords::FloatRange{Floalt64}                       : y-coordinate vector
* thickness:: Float64                                  : Thickness of plate
```

### Optional additional data dictionary keys

```julia
* penalty = 1e20               : Penalty used for fixed degrees of freedoms
* etype::Vector{Int}         : Element material vector if np_types > 1
```

### Return values

```julia
* (fm_df, sigma_df)            : Tuple of jFem, dis_df and fm_df
                                  where:
                                    fm_df         : Forces and moments data table
                                    sigma_df      : Stresses data table
```

### Related help

```julia
?StructuralElement             : List of available structural element types
?Plane                         : Help on a Plane structural element
?FiniteElement                 : List finite element types
?Quadrilateral                 : Help on Quadrilateral finite element
```
