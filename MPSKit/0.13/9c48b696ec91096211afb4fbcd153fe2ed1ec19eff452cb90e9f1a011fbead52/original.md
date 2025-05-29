```
entanglementplot(state; site=0[, kwargs...])
```

Plot the [entanglement spectrum](@ref entanglement_spectrum) of a given MPS `state`. 

# Arguments

  * `state`: the MPS for which to compute the entanglement spectrum.

# Keyword Arguments

  * `site::Int=0`: MPS index for multisite unit cells. The spectrum is computed for the bond between `site` and `site + 1`.
  * `expand_symmetry::Logical=false`: add quantum dimension degeneracies.
  * `sortby=maximum`: the method of sorting the sectors.
  * `sector_margin=1//10`: the amount of whitespace between sectors.
  * `sector_formatter=string`: how to convert sectors to strings.
  * `kwargs...`: other kwargs are passed on to the plotting backend.

!!! note
    You will need to manually import [Plots.jl](https://github.com/JuliaPlots/Plots.jl) to be able to use this function. MPSKit.jl defines its plots based on [RecipesBase.jl](https://github.com/JuliaPlots/Plots.jl/tree/v2/RecipesBase), but the user still has to add `using Plots` to be able to actually produce the plots.

