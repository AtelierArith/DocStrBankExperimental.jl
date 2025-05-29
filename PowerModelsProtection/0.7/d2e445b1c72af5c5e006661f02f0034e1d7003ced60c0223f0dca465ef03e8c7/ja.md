```
parse_matpower(
    file::String;
    method::Union{String,Missing},
    add_gensub::Bool=false,
    flat_start::Bool=false,
    neglect_line_charging::Bool=false,
    neglect_transformer::Bool=false,
    zero_gen_setpoints::Bool=false,
    import_all::Bool=true
)::Dict{String,Any}
```

matpower（送電）ファイルのパーサーです。

`method`はmatpowerファイル用で、"PMs"、"solar-pf"、"dg-pf"、"pf"、または"opf"のいずれかである必要があり、dssファイルの場合は"PMD"またはmissingである必要があります。

`add_gensub`がtrueの場合、[`parse_matpower`](@ref parse_matpower)はgensub辞書からrsとxsを見つけようとします。

`flat_start`、`neglect_line_charging`、`neglect_transformer`、および`zero_gen_setpoints`の説明は、[`prepare_transmission_data!`](@ref prepare_transmission_data!)で見つけることができます。

`add_gensub`がtrueの場合、[`parse_matpower`](@ref parse_matpower)はgensub辞書からrsとxsを見つけようとします。

`flat_start`、`neglect_line_charging`、`neglect_transformer`、および`zero_gen_setpoints`の説明は、[`prepare_transmission_data!`](@ref prepare_transmission_data!)で見つけることができます。
