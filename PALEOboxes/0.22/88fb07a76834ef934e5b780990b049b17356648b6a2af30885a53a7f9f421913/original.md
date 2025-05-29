```
RateStoich(
    ratevartemplate, stoich_statevarname;
    deltavarname_eta=nothing, prcessname="", sms_prefix="", sms_suffix="_sms"
) -> RateStoich
```

Calculate fluxes for a biogeochemical reaction given rate, stoichiometry, and optionally isotope eta.

Add to a Reaction using [`create_ratestoich_method`](@ref) and [`add_method_do!`](@ref).  

A Property Variable should be set to provide the reaction rate (often this is implemented by another method of the same Reaction). This method will then link to that (using the local and link names supplied by `ratevartemplate`) and calculate the appropriate product rates, omitting products that are not present (`VariableReaction` not linked) in the `Model` configuration. Metadata for use when analysing model output should be added to the rate variable using [`add_rate_stoichiometry!`](@ref), in the usual case where this Variable is supplied as `ratevartemplate` this will happen automatically.

# Arguments:

  * `ratevartemplate::Union{VarPropT, VarDepT}`: used to define the rate variable local and link names.
  * `stoich_statevarname`: collection of Tuple(stoichiometry, name) eg ((-2.0, "O2"), (-1.0,"H2S::Isotope"), (1.0, "SO4::Isotope"))
  * `deltavarname_eta`: optional tuple of variable delta + eta ("SO4_delta", -30.0) or ("SO4_delta", rj.pars.delta). If a Parameter is supplied, this is read in `do_react_ratestoich` to allow modification.
  * `processname::String`: optional tag to identify the type of reaction in model output
  * `add_rate_stoichiometry=true`: `true` to add call [`add_rate_stoichiometry!`](@ref) to add metadata to `ratevartemplate`.

# Examples:

Create a `RateStoich` representing the reaction   2 O2 + H2S -> H2SO4

```jldoctest; setup = :(import PALEOboxes)
julia> myratevar = PALEOboxes.VarProp("myrate", "mol yr-1", "a rate");

julia> rs = PALEOboxes.RateStoich(myratevar, ((-2.0, "O2"), (-1.0,"H2S"), (1.0, "SO4")));

julia> rs.stoich_statevarname
((-2.0, "O2"), (-1.0, "H2S"), (1.0, "SO4"))
```
