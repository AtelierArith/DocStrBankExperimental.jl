```
function nodevalues!(
	target::AbstractArray{<:Real,2},
	source::AbstractArray{T,1},
	FE::FESpace{Tv,Ti,FEType,AT},
	operator::Type{<:AbstractFunctionOperator} = Identity;
	regions::Array{Int,1} = [0],
	abs::Bool = false,
	factor = 1,
	target_offset::Int = 0,   # start to write into target after offset
	zero_target::Bool = true, # target vector is zeroed
	continuous::Bool = false)
```

Evaluates the finite element function with the coefficient vector source (interpreted as a coefficient vector for the FESpace FE) and the specified FunctionOperator at all the nodes of the (specified regions of the) grid and writes the values into target. Discontinuous (continuous = false) quantities are evaluated in all neighbouring cells of each node and then averaged. Continuous (continuous = true) quantities are only evaluated once at each node.
