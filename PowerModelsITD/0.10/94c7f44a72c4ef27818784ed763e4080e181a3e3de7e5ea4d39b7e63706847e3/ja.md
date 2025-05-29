```
function solve_mn_dmld_opfitd_simple(
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

最小負荷デルタ（dmld連続）を用いたマルチネットワーク統合T&D最適電力フローを解決します。
