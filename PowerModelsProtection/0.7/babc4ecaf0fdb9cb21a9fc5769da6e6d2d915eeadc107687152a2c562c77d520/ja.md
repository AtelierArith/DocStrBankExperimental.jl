```
parse_file(
    file::String;
    method::Union{String,Missing}=missing,
    add_gensub::Bool=false,
    flat_start::Bool=false,
    neglect_line_charging::Bool=false,
    neglect_transformer::Bool=false,
    zero_gen_setpoints::Bool=false,
    import_all::Bool=true,
    kwargs...
)
```

dss（配電）またはmatpower（送電）ファイルからデータを解析するための関数です。

`method`はmatpowerファイル用で、"PMs"、"solar-pf"、"dg-pf"、"pf"、または"opf"のいずれかである必要があり、dssファイルの場合は"PMD"またはmissingである必要があります。

`add_gensub`がtrueの場合、[`parse_matpower`](@ref parse_matpower)はgensub辞書からrsとxsを見つけようとします。

`flat_start`、`neglect_line_charging`、`neglect_transformer`、および`zero_gen_setpoints`の説明は、[`prepare_transmission_data!`](@ref prepare_transmission_data!)にあります。
