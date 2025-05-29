```julia
mutable struct fuselage_tank
```

Fuselage tank component. Usually for Hydrogen aircraft

  * `fueltype::String`: Fuel type name
  * `tank_count::Int64`: Fuel tank count
  * `placement::String`: Fuel tank location
  * `sizes_insulation::Bool`: Flag for insulation sizing
  * `Wfuelintank::Float64`: Weight of fuel in one tank (N)
  * `clearance_fuse::Float64`
  * `t_insul::Vector{Float64}`: Vector with insulation layer thickness (m)
  * `material_insul::Vector{TASOPT.materials.ThermalInsulator}`: Vector with insulation materials
  * `iinsuldes::Vector{Int64}`: Vector with insulation layer design indices
  * `inner_material::TASOPT.materials.StructuralAlloy`: Inner vessel material
  * `outer_material::TASOPT.materials.StructuralAlloy`: Outer vessel material
  * `ARtank::Float64`: Tank head aspect ratio
  * `theta_inner::Float64`: Angular location of inner vessel stiffeners
  * `theta_outer::Vector{Float64}`: Vector with angular location of outer vessel stiffeners
  * `Ninterm::Float64`: Number of intermediate stiffeners in outer vessel
  * `pvent::Float64`: Venting pressure (Pa)
  * `pinitial::Float64`: Fill pressure (Pa)
  * `pmin::Float64`: Minimum allowable tank pressure (Pa)
  * `t_hold_orig::Float64`: Departure hold time (s)
  * `t_hold_dest::Float64`: Arrival hold time (s)
  * `TSLtank::Float64`: Sea-level temperature used to design tank (K)
  * `rhofuel::Float64`: Liquid fuel density (kg/m^3)
  * `Tfuel::Float64`: Liquid fuel temperature in tank (K)
  * `rhofuelgas::Float64`: Gas fuel density (kg/m^3)
  * `hvap::Float64`: Fuel specific enthalpy of vaporization (J/kg)
  * `boiloff_rate::Float64`: Percentage tank boiloff rate at start of cruise (%/h)
  * `ftankadd::Float64`: Vessel additional mass fraction
  * `ew::Float64`: Vessel weld efficiency
  * `ullage_frac::Float64`: Minimum ullage fraction
  * `qfac::Float64`: Heat leakage factor
  * `pfac::Float64`: Pressure rise factor
