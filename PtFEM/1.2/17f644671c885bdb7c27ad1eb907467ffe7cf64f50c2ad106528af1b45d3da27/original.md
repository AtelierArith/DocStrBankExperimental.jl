# Method p45

Analysis of elasto-plastic beams or rigid-jointed frames using a 2-node Frame structural element in 1, 2 or 3 dimensions. 

### Constructors

```julia
p45(data)
```

### Arguments

```julia
* `data::Dict{Symbol, Any}`  : Dictionary containing all input data
```

### Required data dictionary keys

```julia
* struc_el::StructuralElement                          : Type of  structural element
* support::Array{Tuple{Int,Array{Int,1}},1}        : Fixed-displacements vector
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : Node load vector
* properties::Vector{Float64}                          : Material properties
* x_coords::FloatRange{Float64}                        : x-coordinate vector
* dload::FloatRange{Float64}                           : load steps
```

### Optional additional data dictionary keys

```julia
* penalty = 1e20                 : Penalty used for fixed degrees of freedoms
* etype::Vector{Int}           : Element material vector if np_types > 1
* y_coords::FloatRange{Float64}  : y-coordinate vector (2D)
* z_coords::FloatRange{Float64}  : x-coordinate vector (3D)
* limit = 250                    : Iteration limit
* tol = 0.0001                   : Tolerance for iteration convergence
```

### Related help

```julia
?StructuralElement             : List of available structural element types
?Frame                         : Help on a Frame structural element
?FiniteElement                 : List finite element types
?Line                          : Help on Line finite element
```
