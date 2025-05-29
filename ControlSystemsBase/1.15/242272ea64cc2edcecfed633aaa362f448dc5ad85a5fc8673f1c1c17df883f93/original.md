```
fig = nicholsplot{T<:LTISystem}(systems::Vector{T}, w::AbstractVector; kwargs...)
```

Create a Nichols plot of the `LTISystem`(s). A frequency vector `w` can be optionally provided.

Keyword arguments:

```
text = true
Gains = [12, 6, 3, 1, 0.5, -0.5, -1, -3, -6, -10, -20, -40, -60]
pInc = 30
sat = 0.4
val = 0.85
fontsize = 10
```

`pInc` determines the increment in degrees between phase lines.

`sat` ∈ [0,1] determines the saturation of the gain lines

`val` ∈ [0,1] determines the brightness of the gain lines

Additional keyword arguments are sent to the function plotting the systems and can be used to specify colors, line styles etc. using regular RecipesBase.jl syntax

This function is based on code subject to the two-clause BSD licence Copyright 2011 Will Robertson Copyright 2011 Philipp Allgeuer
