```
chamber(composition::Union{Silicic,Mafic}, end_time::Float64, log_volume_km3_vector::Union{Float64,Vector{Float64}}, InitialConc_H2O_vector::Union{Float64,Vector{Float64}}, InitialConc_CO2_vector::Union{Float64,Vector{Float64}}, log_vfr_vector::Union{Float64,Vector{Float64}}, depth_vector::Union{Float64,Vector{Float64}}, output_dirname::String; kwargs...)
```

Simulate the eruption of a volcano using a model for the frequency of eruptions of upper crustal magma chambers based on Degruyter and Huber (2014).

## Arguments

  * `composition`: The magma composition. Use `Silicic()` for rhyolite composition (arc magma) or `Mafic()` for basalt composition (rift).
  * `end_time`: Maximum magma chamber evolution duration in seconds.
  * `log_volume_km3`: The initial volume of the chamber in logarithmic scale. The actual initial chamber volume is calculated as 10^(`log_volume_km3`) in km³.
  * `InitialConc_H2O`: The initial weight fraction of water in the magma (exsolved + dissolved).
  * `InitialConc_CO2`: The initial weight fraction of CO₂ in the magma (exsolved + dissolved).
  * `log_vfr`: Magma recharge rate in km³/yr calculated as 10^(`log_vfr`).
  * `depth`: Depth of the magma chamber in meters.
  * `output_dirname`(optional): Name of the output directory. Defaults to current timestamp.

## Keyword Arguments

  * `plotfig`(optional): (default: `true`). Generate and plot figures for each result if true.

## Returns

A `DataFrame` containing the solution with columns:

  * `time`: Simulation timestamps in seconds.
  * `P+dP`: Pressure in Pa.
  * `T`: Temperature in K.
  * `eps_g`: Gas volume fraction.
  * `V`: Volume of the magma chamber in m³.
  * `rho_m`: Density of the melt in kg/m³.
  * `rho_x`: Density of magma crystal in kg/m³.
  * `X_CO2`: Mole fraction of CO2 in the gas.
  * `total_mass`: Total mass of magma chamber in kg.
  * `total_mass_H2O`: Total mass of water in the magma in kg.
  * `total_mass_CO2`: Total mass of CO₂ in the magma in kg.
  * `eps_x`: Crystal volume fraction.

## Outputs

A directory named after `output_dirname` or the default value, containing the following files:

  * `out.csv`: a CSV file containing the solution columns listed above.
  * `eruptions.csv`, A CSV file containing the datas of eruptions with the following columns: time*of*eruption (sec), duration*of*eruption (sec), mass*erupted (kg) and volume*erupted (km³).
  * Figures for P+dP(t), T(t), eps*g(t), V(t), X*CO2(t), total_mass(t).

## References

  * W. Degruyter and C. Huber (2014). A model for eruption frequency of upper crustal silicic magma chambers. Earth Planet. Sci. Lett. https://doi.org/10.1016/j.epsl.2014.06.047

## Examples

```
# Run a simulation with silicic magma chamber
julia> composition = Silicic()
julia> end_time = 3e9
julia> log_volume_km3 = 0.2
julia> InitialConc_H2O = [0.04, 0.045]
julia> InitialConc_CO2 = [0.001, 0.0012]
julia> log_vfr = -3.3
julia> depth = 8e3

julia> chamber(composition, end_time, log_volume_km3, InitialConc_H2O, InitialConc_CO2, log_vfr, depth)

# Run a simulation with mafic magma chamber, with custom directory name "MyDirname"
julia> composition = Mafic()
julia> end_time = 3e9
julia> log_volume_km3 = 0.2
julia> InitialConc_H2O = [0.01, 0.012]
julia> InitialConc_CO2 = 0.001
julia> log_vfr = -3.3
julia> depth = [7e3, 8e3]
julia> output_dirname = "MyDirname"

julia> chamber(composition, end_time, log_volume_km3, InitialConc_H2O, InitialConc_CO2, log_vfr, depth, output_dirname)
```
