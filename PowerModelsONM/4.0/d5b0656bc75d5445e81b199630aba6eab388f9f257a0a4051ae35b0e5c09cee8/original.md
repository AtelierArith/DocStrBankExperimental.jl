```
transform_data_model(eng::T; global_keys::Set{String}=Set{String}(), eng2math_passthrough::Dict{String,<:Vector{<:String}}=Dict{String,Vector{String}}(), kwargs...)::T where T <: Dict{String,Any}
```

ONM-specific version of `PowerModelsDistribution.transform_data_model` that includes the necessary default `eng2math_passthrough` and `global_keys`.
