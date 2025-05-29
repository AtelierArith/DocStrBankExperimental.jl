```
PropsSI(fluid::AbstractString, output::AbstractString)
```

Return a value that does not depend on the thermodynamic state - this is a convenience function that does the call `PropsSI(output, "", 0, "", 0, fluid)`.

# Arguments

  * `fluid::AbstractString`: The name of the fluid that is part of CoolProp, for instance "n-Propane", to get a list of possible values types call `get_global_param_string(key)` with `key` one of the following: `["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`, also there is a list in CoolProp online documentation [List of Fluids](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids), or simply type `?CoolProp_fluids`
  * `output::AbstractString`: The name of parameter to evaluate. to see a list type `?CoolProp_parameters`

# Example

```julia
julia> PropsSI("n-Butane", "rhomolar_critical")
3922.769612987809
```

# Ref

CoolProp::Props1SI(std::string, std::string)
