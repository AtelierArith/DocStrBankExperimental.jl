```
transferplot(above, below=above; sectors=[], transferkwargs=(;)[, kwargs...])
```

Plot the partial transfer matrix spectrum of two InfiniteMPS's.

# Arguments

  * `above::InfiniteMPS`: above mps for [`transfer_spectrum`](@ref).
  * `below::InfiniteMPS=above`: below mps for [`transfer_spectrum`](@ref).

# Keyword Arguments

  * `sectors=[]`: vector of sectors for which to compute the spectrum.
  * `transferkwargs`: kwargs for call to [`transfer_spectrum`](@ref).
  * `kwargs`: other kwargs are passed on to the plotting backend.
  * `thetaorigin=0`: origin of the angle range.
  * `sector_formatter=string`: how to convert sectors to strings.

!!! note
    You will need to manually import [Plots.jl](https://github.com/JuliaPlots/Plots.jl) to be able to use this function. MPSKit.jl defines its plots based on [RecipesBase.jl](https://github.com/JuliaPlots/Plots.jl/tree/v2/RecipesBase), but the user still has to add `using Plots` to be able to actually produce the plots.

