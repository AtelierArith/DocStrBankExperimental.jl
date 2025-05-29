```julia
ismassaction(rx, rs; rxvars = get_variables(rx.rate),
                              haveivdep = nothing,
                              unknownset = Set(unknowns(rs)),
                              ivset = nothing)
```

True if a given reaction is of mass action form, i.e. `rx.rate` does not depend on any chemical species that correspond to unknowns of the system, and does not depend explicitly on the independent variable (usually time).

# Arguments

  * `rx`, the [`Reaction`](@ref).
  * `rs`, a [`ReactionSystem`](@ref) containing the reaction.
  * Optional: `rxvars`, `Variable`s which are not in `rxvars` are ignored as possible dependencies.
  * Optional: `haveivdep`, `true` if the [`Reaction`](@ref) `rate` field explicitly depends on any independent variable (i.e. t or for spatial systems x,y,etc). If not set, will be automatically calculated.
  * Optional: `unknownset`, set of unknowns which if the rxvars are within mean rx is non-mass action.
  * Optional: `ivset`, a `Set` of the independent variables of the system. If not provided and the system is spatial, i.e. `isspatial(rs) == true`, it will be created with all the spatial variables and the time variable. If the rate expression contains any element of `ivset`, then `ismassaction(rx,rs) == false`. Pass a custom set to control this behavior.

Notes:

  * Non-integer stoichiometry is treated as non-mass action. This includes symbolic variables/terms or floating point numbers for stoichiometric coefficients.
