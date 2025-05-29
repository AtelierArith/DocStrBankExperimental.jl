```
function solve_mn_opfitd_storage_linear(
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

ストレージを持つ多ネットワーク統合T&D最適電力フローを線形ストレージモデルで解決します。
