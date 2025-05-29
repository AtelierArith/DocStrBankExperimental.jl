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

SOLPSおよびEFITファイルを収集し、それらをIMAS構造にロードします。必要に応じてプロファイルを外挿して、全体像を把握します。
