# Method p46

Stability (buckling) analysis of elastic beams using a 2-node Beam structural element and Line finite elements. Elastic foundation is optional.

### Constructors

```julia
p46(data)
```

### Arguments

```julia
* `data::Dict{Symbol, Any}` : Dictionary containing all input data
```

### Required data dictionary keys

```julia
* struc_el::StructuralElement                          : Type of  structural fin_el
* support::Array{Tuple{Int,Array{Int,1}},1}        : Fixed-displacements vector
* properties::Vector{Float64}                          : Material properties
* x_coords::FloatRange{Float64}                        : x-coordinate vector
```

### Optional additional data dictionary keys

```julia
* etype::Vector{Int}         : Element material vector if np_types > 1
* limit = 250                  : Iteration limit
* tol = 0.0001                 : Tolerance for iteration convergence
```

### Related help

```julia
?StructuralElement             : List of available structural element types
?Beam                          : Help on a Beam structural element
?FiniteElement                 : List finite element types
?Line                          : Help on Line finite element
```
