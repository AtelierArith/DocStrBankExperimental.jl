```
REoptInputs
```

The data structure for all the inputs necessary to construct the JuMP model.

```julia
struct REoptInputs <: AbstractInputs
    s::AbstractScenario
    techs::Techs
    min_sizes::Dict{String, Float64}  # (techs)
    max_sizes::Dict{String, Float64}  # (techs)
    existing_sizes::Dict{String, Float64}  # (techs)
    cap_cost_slope::Dict{String, Any}  # (techs)
    om_cost_per_kw::Dict{String, Float64}  # (techs)
    time_steps::UnitRange
    time_steps_with_grid::Array{Int, 1}
    time_steps_without_grid::Array{Int, 1}
    hours_per_timestep::Float64
    months::UnitRange
    production_factor::DenseAxisArray{Float64, 2}  # (techs, time_steps)
    levelization_factor::Dict{String, Float64}  # (techs)
    value_of_lost_load_per_kwh::Array{R, 1} where R<:Real #default set to 1 US dollar per kwh
    pwf_e::Float64
    pwf_om::Float64
    third_party_factor::Float64
    pvlocations::Array{Symbol, 1}
    maxsize_pv_locations::DenseAxisArray{Float64, 1}  # indexed on pvlocations
    pv_to_location::Dict{String, Dict{Symbol, Int64}}  # (techs.pv, pvlocations)
    ratchets::UnitRange
    techs_by_exportbin::Dict{Symbol, AbstractArray}  # keys can include [:NEM, :WHL, :CUR]
    export_bins_by_tech::Dict
    n_segs_by_tech::Dict{String, Int}
    seg_min_size::Dict{String, Dict{Int, Float64}}
    seg_max_size::Dict{String, Dict{Int, Float64}}
    seg_yint::Dict{String, Dict{Int, Float64}}
    pbi_pwf::Dict{String, Any}  # (pbi_techs)
    pbi_max_benefit::Dict{String, Any}  # (pbi_techs)
    pbi_max_kw::Dict{String, Any}  # (pbi_techs)
    pbi_benefit_per_kwh::Dict{String, Any}  # (pbi_techs)
    boiler_efficiency::Dict{String, Float64}
end
```
