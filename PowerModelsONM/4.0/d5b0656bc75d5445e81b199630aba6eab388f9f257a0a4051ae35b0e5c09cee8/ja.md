```
transform_data_model(eng::T; global_keys::Set{String}=Set{String}(), eng2math_passthrough::Dict{String,<:Vector{<:String}}=Dict{String,Vector{String}}(), kwargs...)::T where T <: Dict{String,Any}
```

ONM特有の`PowerModelsDistribution.transform_data_model`のバージョンで、必要なデフォルトの`eng2math_passthrough`と`global_keys`が含まれています。
