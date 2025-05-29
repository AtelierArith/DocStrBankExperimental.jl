```
function nodevalues_subset!(
	target::AbstractArray{<:Real,2},
	source::AbstractArray{T,1},
	FE::FESpace{Tv,Ti,FEType,AT},
	operator::Type{<:AbstractFunctionOperator} = Identity;
	regions::Array{Int,1} = [0],
	abs::Bool = false,
	factor = 1,
	nodes = [],				  
	target_offset::Int = 0,   # start to write into target after offset
	zero_target::Bool = true, # target vector is zeroed
	continuous::Bool = false)
```

Evaluates the finite element function with the coefficient vector source (interpreted as a coefficient vector for the FESpace FE) and the specified FunctionOperator at the specified list of nodes of the grid and writes the values in that order into target. Node values for nodes that are not part of the specified regions (default = all regions) are set to zero. Discontinuous (continuous = false) quantities are evaluated in all neighbouring cells (in the specified regions) of each node and then averaged. Continuous (continuous = true) quantities are only evaluated once at each node.
