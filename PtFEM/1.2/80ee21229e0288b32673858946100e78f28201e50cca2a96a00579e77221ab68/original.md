# Method p63_skyline

Plane strain bearing capacity analysis of an elastic-plastic (Mohr-Coulomb) material using 8-node rectangular quadrilaterals. Rigid smooth footing. Displacement control. Viscoplastic strain method.

### Constructors

```julia
p63_skyline(data)
```

### Arguments

```julia
* `data::Dict{Symbol, Any}` : Dictionary containing all input data
```

### Required data dictionary keys

```julia
* struc_el::StructuralElement                          : Structural element
* properties::Vector{Float64}                          : Material properties
* x_coords::FloatRange{Floalt64}                       : x-coordinate vector
* y_coords::FloatRange{Floalt64}                       : y-coordinate vector
```

### Optional additional data dictionary keys

```julia
* tol::Float64                 : Convergence tolerance
* limit = 250                  : Iteration limit
* incs::Int                    : Incremental load steps
* presc::Float64               : Wall displacement increment
* penalty = 1e20               : Penalty used for fixed degrees of freedoms
* etype::Vector{Int}           : Element material vector if np_types > 1
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
