```
function nodevalues!(
    target::AbstractArray{<:Real,2},
    source::FEVectorBlock,
    operator::Type{<:AbstractFunctionOperator} = Identity;
    regions::Array{Int,1} = [0],
    abs::Bool = false,
    factor = 1,
    target_offset::Int = 0,   # start to write into target after offset
    zero_target::Bool = true, # target vector is zeroed
    continuous::Bool = false)
```

Evaluates the finite element function with the coefficient vector source and the specified FunctionOperator at all the nodes of the (specified regions of the) grid and writes the values into target. Discontinuous (continuous = false) quantities are averaged.
