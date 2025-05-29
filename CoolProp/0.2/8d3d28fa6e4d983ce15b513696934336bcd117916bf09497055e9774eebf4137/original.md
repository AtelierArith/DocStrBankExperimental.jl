```
PropsSI(output::AbstractString, name1::AbstractString, value1::Real, name2::AbstractString, value2::Real, fluid::AbstractString)
```

Return a value that depends on the thermodynamic state.

> For pure and pseudo-pure fluids, two state points are required to fix the state. The equations of state are based on T and ρ as state variables, so T, ρ will always be the fastest inputs. P, T will be a bit slower (3-10 times), and then comes inputs where neither T nor ρ are given, like p, h. They will be much slower. If speed is an issue, you can look into table-based interpolation methods using TTSE or bicubic interpolation.


# Arguments

  * `fluid::AbstractString`: The name of the fluid that is part of CoolProp, for instance "n-Propane", to get a list of different passible fulid types call `get_global_param_string(key)` with `key` one of the following: `["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`, also there is a list in CoolProp online documentation [List of Fluids](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids)
  * `output::AbstractString`: The name of parameter to evaluate. to see a list type `?CoolProp_parameters`
  * `name1::AbstractString`: The name of parameter for first state point
  * `value1::Real`: Value of the first state point
  * `name2::AbstractString`: The name of parameter for second state point
  * `value2::Real`: Value of the second state point

# Example

```julia
julia> PropsSI("D", "T", 300, "P", 101325, "n-Butane")
2.4325863624814326
julia> PropsSI("D", "T", 300, "P", 101325, "INCOMP::DEB") # incompressible pure
857.1454
julia> PropsSI("D", "T", 300, "P", 101325, "INCOMP::LiBr[0.23]") # incompressible mass-based binary mixture
1187.5438243617214
julia> PropsSI("D", "T", 300, "P", 101325, "INCOMP::ZM[0.23]") # incompressible volume-based binary mixtures
1028.7273860290911
julia> PropsSI("Dmass", "T", 300, "P", 101325, "R125[0.5]&R32[0.5]")
3.5413381483914512
julia> split(get_global_param_string("mixture_binary_pairs_list"), ', ')[1] # a random binary pair
"100-41-4&106-42-3"
julia> PropsSI("Dmass", "T", 300, "P", 101325, "100-41-4[0.5]&106-42-3[0.5]") # ethylbenzene[0.5]&p-Xylene[0.5]
857.7381127561846
```

# Ref

CoolProp::PropsSI(const std::string &, const std::string &, double, const std::string &, double, const std::string&)
