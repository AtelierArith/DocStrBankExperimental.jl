# Method p61

Plane strain bearing capacity analysis of an elastic-plastic (von Mises) material using 8-node rectangular quadrilaterals. Viscoplastic strain method.

### Constructors

```julia
p61(data)
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
* tol::Float64                                         : Convergence tolerance
* qincs::Vector{Float64}                               : Incremental load steps
```

### Optional additional data dictionary keys

```julia
* limit = 250                  : Iteration limit
* penalty = 1e20               : Penalty used for fixed degrees of freedoms
* etype::Vector{Int}         : Element material vector if np_types > 1
```

### Return values

```julia
* (g_coord, g_num, disp)        : where:
                                    g_coord  : Coordinates
                                    g_num    : Node numbering
                                    disp     : Matrix of displacements
```

### Related help

```julia
?StructuralElement             : List of available structural element types
?Plane                         : Help on a Plane structural element
?FiniteElement                 : List finite element types
?Quadrilateral                 : Help on Quadrilateral finite element
```
