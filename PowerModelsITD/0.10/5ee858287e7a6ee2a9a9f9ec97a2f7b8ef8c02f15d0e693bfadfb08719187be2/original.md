```
function solve_model(
    pmitd_data::Dict{String,<:Any},
    pmitd_type::Type, optimizer,
    build_method::Function;
    multinetwork::Bool=false,
    solution_processors::Vector{<:Function}=Function[],
    pmitd_ref_extensions::Vector{<:Function}=Function[],
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    make_si::Bool=true,
    solution_model::String="eng",
    kwargs...
)
```

Instantiates and solves the integrated Transmission (PowerModels) & Distribution (PowerModelsDistribution) modeling object from power integrated transmission-distribution input data, `pmitd_data`. Here, `pmitd_type` is the integrated power transmission-distribution modeling type, `build_method` is the build method for the problem specification being considered, `multinetwork` is the boolean that defines if the modeling object should be define as multinetwork`, solution_processors` is the vector of the model solution processors, `pmitd_ref_extensions` is the array of modeling extensions, and `make_si` is the boolean that determines if the results are returned in SI or per-unit. `eng2math_passthrough` are the passthrough vectors to be considered by the PMD MATH models. `solution_model` is a string that determines in which model, ENG or MATH, the solutions are presented. Returns a dictionary of results.
