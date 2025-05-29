# Method p41

One dimensional analysis of an axially loaded elastic Rod using 2-node  Line elements. 

### Constructors

```julia
p41(m, data) # Re-use factored global stiffness matrix
```

### Arguments

```julia
* `m::jFEM`                  : Previously created jFEM model
* `data::Dict{Symbol, Any}`  : Dictionary containing all input data
```

### Required data dictionary keys

```julia
* struc_el::StructuralElement                          : Type of  structural fin_el
* support::Array{Tuple{Int,Array{Int,1}},1}        : Fixed-displacements vector
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : Node load vector
* properties::Vector{Float64}                          : Material properties
* x_coords::FloatRange{Float64}                        : x-coordinate vector
```

### Optional additional data dictionary keys

```julia
* penalty = 1e20               : Penalty used for fixed degrees of freedoms
* etype::Vector{Int}         : Element material vector if np_types > 1
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
?StructuralElement             : List of available structural element types
?Rod                           : Help on a Rod structural element
?FiniteElement                 : List finite element types
?Line                          : Help on Line finite element
```
