# p44

Analysis of elastic rigid-jointed frames using a 2-node Frame structural element and Line finite elements in 2 or 3 dimensions.

### Constructors

```julia
p44(data)
```

### Arguments

```julia
* `data::Dict{Symbol, Any}` : Dictionary containing all input data
```

### Dictionary keys

```julia
* struc_el::StructuralElement                          : Type of  structural fin_el
* support::Array{Tuple{Int,Array{Int,1}},1}        : Fixed-displacements vector
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : Node load vector
* properties::Vector{Float64}                          : Material properties
* x_coords::FloatRange{Float64}                        : x coordinate vector
* y_coords::FloatRange{Float64}                        : y coordinate vector
* g_num::Array{Int,2}                                : Element node connections
* fixed_freedoms::Array{Tuple{Vector{Int}}           : Fixed freedoms
```

### Optional additional dictionary keys

```julia
* etype::Vector{Int}                                 : Element material vector
* penalty::Float64                                     : Penalty for fixed freedoms
* z_coords::FloatRange{Float64}                        : z coordinate vector
* eq_nodal_forces_and_moments                          : Equivalent nodal loads
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
?StructuralElement  : Help on structural elements
?Beam               : Help on a Beam structural fin_el
?FiniteElement      : Help on finite element types
```
