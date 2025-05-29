```
function instantiate_model(
    pmitd_data::Dict{String,<:Any},
    pmitd_type::Type,
    build_method::Function;
    multinetwork::Bool=false,
    pmitd_ref_extensions::Vector{<:Function}=Function[],
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    kwargs...
)
```

Instantiates and returns PowerModelsITD modeling object from parsed power transmission and distribution (PMITD) input data `pmitd_data`. Here, `pmitd_type` is the integrated power transmission and distribution modeling type and `build_method` is the build method for the problem specification being considered. `multinetwork` is the boolean that defines if the modeling object should be define as multinetwork. `pmitd_ref_extensions` is an array of power transmission and distribution modeling extensions. `eng2math_passthrough` are the passthrough vectors to be considered by the PMD MATH models.
