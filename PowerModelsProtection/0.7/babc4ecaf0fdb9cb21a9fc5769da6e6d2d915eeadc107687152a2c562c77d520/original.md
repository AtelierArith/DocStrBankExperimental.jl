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

Function to parse data from `dss` (distribution) or `matpower` (transmission) files.

`method` is for matpower files, and should be one of "PMs", "solar-pf", "dg-pf", "pf", or "opf", and "PMD" or missing for dss files.

If `add_gensub`, [`parse_matpower`](@ref parse_matpower) will attempt to find rs and xs from a gensub dict.

Explanations of `flat_start`, `neglect_line_charging`, `neglect_transformer`, and `zero_gen_setpoints` can be found in [`prepare_transmission_data!`](@ref prepare_transmission_data!)
