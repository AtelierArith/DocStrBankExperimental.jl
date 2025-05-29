```
visualize(lc::LinearChain, axis::String, modes::Vector{<:Int}, format="bars")
```

Visualize the normal mode structure of a `lc` as a Plots.jl plot. `axis` can either be one of "x", "y", "z" or a NamedTuple{(:x,:y,:z)}. `modes` is a vector of indices  selecting which modes should be included in the plot. Slicing is supported. `format` can be  either "bars" or "circles."

Note that the indexing refers to the full normal mode description and not the subset  `selectedmodes(lc)`.
