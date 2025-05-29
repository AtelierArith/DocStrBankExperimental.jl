```
function instantiate_model(
    pm_file::String,
    pmd_file::String,
    pmitd_file::String,
    pmitd_type::Type,
    build_method::Function;
    multinetwork::Bool=false,
    pmitd_ref_extensions::Vector{<:Function}=Function[],
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    auto_rename::Bool=false,
    kwargs...
)
```

Instantiates and returns PowerModelsITD modeling object from power transmission, power distribution, and boundary linking input files `pm_file`, `pmd_file` (one file provided), and `pmitd_file`, respectively. Here, `pmitd_type` is the integrated power transmission-distribution modeling type and `build_method` is the build method for the problem specification being considered. `multinetwork` is the boolean that defines if the modeling object should be define as multinetwork. `pmitd_ref_extensions` are the arrays of power transmission and distribution modeling extensions. `eng2math_passthrough` are the passthrough vectors to be considered by the PMD MATH models.
