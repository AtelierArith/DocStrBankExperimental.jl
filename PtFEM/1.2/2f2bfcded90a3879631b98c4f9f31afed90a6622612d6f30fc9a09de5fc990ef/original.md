# Method p51_skyline

Plane or axisymmetric strain analysis of an elastic solid (Plane structural element) using 3-, 6-, 10- or 15-node right-angled triangles (Triangle finite elements) or 4-, 8- or 9-node rectangular quadrilaterals (Quadrilateral finite elements). Mesh numbered in x(r)- or y(z)- direction.

### Constructors

```julia
p51(data)
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
* etype::Vector{Int}           : Element material vector if np_types > 1
```

### Return values

```julia
* fem                          : Fem object
```

### Related help

```julia
?StructuralElement             : List of available structural element types
?Plane                         : Help on a Plane structural element
?FiniteElement                 : List finite element types
?Quadrilateral                 : Help on Quadrilateral finite element
```
