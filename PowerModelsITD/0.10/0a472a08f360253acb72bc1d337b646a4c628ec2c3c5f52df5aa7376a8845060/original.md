```
function solve_opfitd_storage(
    pm_file,
    pmd_file,
    pmitd_file,
    pmitd_type,
    optimizer;
    solution_processors::Vector{<:Function}=Function[],
    pmitd_ref_extensions::Vector{<:Function}=Vector{Function}([]),
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    make_si::Bool=true,
    auto_rename::Bool=false,
    solution_model::String="eng",
    kwargs...
)
```

Solve Integrated T&D Optimal Power Flow with Storage OPF Dispatch.
