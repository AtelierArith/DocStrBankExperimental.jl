```
REoptInputs
```

The data structure for all the inputs necessary to construct the JuMP model.

```julia
struct REoptInputs <: AbstractInputs
    s::ScenarioType
    techs::Techs
    min_sizes::Dict{String, <:Real}  # (techs)
    max_sizes::Dict{String, <:Real}  # (techs)
    existing_sizes::Dict{String, <:Real}  # (techs)
    cap_cost_slope::Dict{String, Any}  # (techs)
    om_cost_per_kw::Dict{String, <:Real}  # (techs)
    thermal_cop::Dict{String, <:Real}  # (techs.absorption_chiller)
    time_steps::UnitRange
    time_steps_with_grid::Array{Int, 1}
    time_steps_without_grid::Array{Int, 1}
    hours_per_time_step::Real
    months::UnitRange
    production_factor::DenseAxisArray{<:Real, 2}  # (techs, time_steps)
    levelization_factor::Dict{String, <:Real,}  # (techs)
    value_of_lost_load_per_kwh::Array{<:Real, 1}
    pwf_e::Real
    pwf_om::Real
    pwf_fuel::Dict{String, <:Real}
    pwf_emissions_cost::Dict{String, Float64} # Cost of emissions present worth factors for grid and onsite fuelburn emissions [unitless]
    pwf_grid_emissions::Dict{String, Float64} # Emissions [lbs] present worth factors for grid emissions [unitless]
    pwf_offtaker::Real 
    pwf_owner::Real
    third_party_factor::Real
    pvlocations::Array{Symbol, 1}
    maxsize_pv_locations::DenseAxisArray{<:Real, 1}  # indexed on pvlocations
    pv_to_location::Dict{String, Dict{Symbol, Int64}}  # (techs.pv, pvlocations)
    ratchets::UnitRange
    techs_by_exportbin::Dict{Symbol, AbstractArray}  # keys can include [:NEM, :WHL, :CUR]
    export_bins_by_tech::Dict
    n_segs_by_tech::Dict{String, Int}
    seg_min_size::Dict{String, Dict{Int, <:Real}}
    seg_max_size::Dict{String, Dict{Int, <:Real}}
    seg_yint::Dict{String, Dict{Int, <:Real}}
    pbi_pwf::Dict{String, Any}  # (pbi_techs)
    pbi_max_benefit::Dict{String, Any}  # (pbi_techs)
    pbi_max_kw::Dict{String, Any}  # (pbi_techs)
    pbi_benefit_per_kwh::Dict{String, Any}  # (pbi_techs)
    boiler_efficiency::Dict{String, <:Real}
    fuel_cost_per_kwh::Dict{String, AbstractArray}  # Fuel cost array for all time_steps
    ghp_options::UnitRange{Int64}  # Range of the number of GHP options
    require_ghp_purchase::Int64  # 0/1 binary if GHP purchase is forced/required
    ghp_heating_thermal_load_served_kw::Array{Float64,2}  # Array of heating load (thermal!) profiles served by GHP
    ghp_cooling_thermal_load_served_kw::Array{Float64,2}  # Array of cooling load profiles served by GHP
    space_heating_thermal_load_reduction_with_ghp_kw::Array{Float64,2}  # Array of heating load reduction (thermal!) profile from GHP retrofit
    cooling_thermal_load_reduction_with_ghp_kw::Array{Float64,2}  # Array of cooling load reduction (thermal!) profile from GHP retrofit
    ghp_electric_consumption_kw::Array{Float64,2}  # Array of electric load profiles consumed by GHP
    ghp_installed_cost::Array{Float64,1}  # Array of installed cost for GHP options
    ghp_om_cost_year_one::Array{Float64,1}  # Array of O&M cost for GHP options    
    tech_renewable_energy_fraction::Dict{String, <:Real} # union(techs.elec, techs.fuel_burning)
    tech_emissions_factors_CO2::Dict{String, <:Real} # (techs)
    tech_emissions_factors_NOx::Dict{String, <:Real} # (techs)
    tech_emissions_factors_SO2::Dict{String, <:Real} # (techs)
    tech_emissions_factors_PM25::Dict{String, <:Real} # (techs)
    techs_operating_reserve_req_fraction::Dict{String, <:Real} # (techs.all)
    heating_cop::Dict{String, Array{<:Real, 1}} # (techs.ashp)
    cooling_cop::Dict{String, Array{<:Real, 1}} # (techs.ashp)
    heating_cf::Dict{String, Array{<:Real, 1}} # (techs.ashp)
    cooling_cf::Dict{String, Array{<:Real, 1}} # (techs.ashp)
    heating_loads_kw::Dict{String, <:Real} # (heating_loads)
    unavailability::Dict{String, Array{Float64,1}}  # Dict by tech of unavailability profile
end
```
