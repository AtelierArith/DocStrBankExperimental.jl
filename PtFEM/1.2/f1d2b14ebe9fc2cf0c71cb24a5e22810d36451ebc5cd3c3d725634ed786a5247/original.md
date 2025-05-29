# Method p42

Analysis of elastic pin-jointed frames using 2-node rod elements in 2- or 3-dimensions.

### Constructors

```julia
p42(data)
```

### Arguments

```julia
* `data::Dict{Symbol, Any}`  : Dictionary containing all input data
```

### Dictionary keys

```julia
* struc_el::StructuralElement                          : Type of structural element
* support::Array{Tuple{Int,Array{Int,1}},1}        : Fixed-displacements vector
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : Node load vector
* properties::Vector{Float64}                          : Material properties
* x_coords::Vector{Float64}                            : x coordinate vector
* y_coords::Vector{Float64}                            : y coordinate vector
* g_num::Array{Int,2}                                : Element node connections
```

### Optional additional dictionary keys

```julia
* penalty::Float64             : Penalty for fixed freedoms
* etype::Vector{Int}         : Element material vector
* z_coords::Vector{Float64}    : z coordinate vector (3D)
* eq_nodal_forces_and_moments  : Contribution of distributed loads to loaded_nodes
```

### Return values

```julia
* (jfem, dis_df, fm_df)        : Tuple of jFem, dis_df and fm_df
                                 where:
                                    jfem::jFem    : Computational result type
                                    dis_df        : Displacement data table
                                    fm_df         : Forces and moments data table
```

### Related help

```julia
?StructuralElement  : List structural element types
?Frame              : Help on a Rod structural fin_el
?FiniteElement      : List finite element types
?Line               : Help on Line finite element
```
