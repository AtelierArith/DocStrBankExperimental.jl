```
function nodevalues(
	source::FEVectorBlock,
	operator::Type{<:AbstractFunctionOperator} = Identity;
	regions::Array{Int,1} = [0],
	abs::Bool = false,
	factor = 1,
	nodes = [],				  
	cellwise = false,		  # return cellwise nodevalues ncells x nnodes_on_cell (only if nodes == [])
	target_offset::Int = 0,   # start to write into target after offset
	zero_target::Bool = true, # target vector is zeroed
	continuous::Bool = false)
```

Evaluates the finite element function with the coefficient vector source and the specified FunctionOperator at the specified list of nodes of the grid (default = all nodes) and writes the values in that order into target. Nodes that are not part of the specified regions (default = all regions) are set to zero. Discontinuous (continuous = false) quantities are evaluated in all neighbouring cells of each node and then averaged. Continuous (continuous = true) quantities are only evaluated once at each node.
