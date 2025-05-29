```
PhaseSI(name1::AbstractString, value1::Real, name2::AbstractString, value2::Real, fluid::AbstractString)
```

Return a string representation of the phase. Valid states are: "liquid", "supercritical", "supercritical*gas", "supercritical*liquid", "critical_point", "gas", "twophase"

# Arguments

  * `fluid::AbstractString`: The name of the fluid that is part of CoolProp, for instance "n-Propane", to get a list of different passible fulid types call `get_global_param_string(key)` with `key` one of the following: `["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`, also there is a list in CoolProp online documentation [List of Fluids](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids)
  * `name1::AbstractString`: The name of parameter for first state point
  * `value1::Real`: Value of the first state point
  * `name2::AbstractString`: The name of parameter for second state point
  * `value2::Real`: Value of the second state point

# Example

```julia
julia> PhaseSI("T", PropsSI("TCRIT", "Water"), "P", PropsSI("PCRIT", "Water"), "Water")
"critical_point"
julia> PhaseSI("T", 300, "Q", 1, "Water")
"twophase"
julia> PhaseSI("P", "T", 300, "Q", 1, "Water")
3536.806750422325
julia> PhaseSI("T", 300, "P", 3531, "Water")
"gas"
julia> PhaseSI("T", 300, "P", 3541, "Water")
"liquid"
```

# Ref

CoolProp::PhaseSI(const std::string &, double, const std::string &, double, const std::string&)
