```
AbstractState_factory(backend::AbstractString, fluids::AbstractString)
```

Generate an AbstractState instance return an integer handle to the state class generated to be used in the other low-level accessor functions.

# Arguments

  * `backend`: The backend you will use could be: `["HEOS", "REFPROP", "INCOMP", "IF97", "TREND", "HEOS&TTSE", "HEOS&BICUBIC", "SRK", "PR", "VTPR"]` etc.
  * `fluids`: '&' delimited list of fluids. To get a list of possible values call `get_global_param_string(key)` with `key` one of the following: `["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`, also there is a list in CoolProp online documentation [List of Fluids](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids), or simply type `?CoolProp_fluids`

# Example

```julia
julia> HEOS = AbstractState_factory("HEOS", "R245fa");
julia> TTSE = AbstractState_factory("HEOS&TTSE", "R245fa");
julia> BICU = AbstractState_factory("HEOS&BICUBIC", "R245fa");
julia> SRK = AbstractState_factory("SRK", "R245fa");
julia> PR = AbstractState_factory("PR", "R245fa");
```
