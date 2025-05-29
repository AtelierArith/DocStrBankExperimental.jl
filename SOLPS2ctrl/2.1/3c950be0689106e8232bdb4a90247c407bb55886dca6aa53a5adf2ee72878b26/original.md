```
preparation(
    eqdsk_file::String,
    dirs::String...;
    core_method::String="simple",
    filename::String="sd_input_data",
    output_format::String="json",
    eqdsk_set_time::Union{Nothing, Float64}=nothing,
    eq_time_index::Int=1,
    allow_boundary_flux_correction::Bool=false,
)::IMAS.dd
```

Gathers SOLPS and EFIT files and loads them into IMAS structure. Extrapolates profiles as needed to get a complete picture.
