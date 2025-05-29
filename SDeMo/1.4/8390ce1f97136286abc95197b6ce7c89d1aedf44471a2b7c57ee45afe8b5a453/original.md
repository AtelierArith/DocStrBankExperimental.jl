```
variables!(model::M, ::Type{StrictVarianceInflationFactor{N}}, args...; included::Vector{Int}=Int[], optimality=mcc, verbose::Bool=false, bagfeatures::Bool=false, kwargs...) where {M <: Union{SDM, Bagging}, N}
```

Version of the variable selection for the strict VIF case. This may result in a worse model, and for this reason there is no cross-validation.
