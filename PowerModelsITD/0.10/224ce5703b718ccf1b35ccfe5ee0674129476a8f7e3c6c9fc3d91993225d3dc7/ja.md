```
function solve_opfitd_storage_linear(
    pmitd_data::Dict{String,<:Any},
    pmitd_type,
    optimizer;
    solution_processors::Vector{<:Function}=Function[],
    pmitd_ref_extensions::Vector{<:Function}=Vector{Function}([]),
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    make_si::Bool=true,
    solution_model::String="eng",
    kwargs...
)
```

ストレージの線形モデルを用いた統合T&D最適電力フローの解決。
