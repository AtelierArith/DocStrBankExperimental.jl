```
C = cpt4dcw(codes::String, vals::Vector{<:Real}; kwargs...)
```

Create a categorical CPT to use with the output of `coast(dcw=...)` to make Choropleth maps.

  * `codes` is a comma separated string with two chars country codes (ex: "PT,ES,FR,IT")
  * `vals` a vector with same size as country codes, with the values used to colorize the countries

Optionally provide a CPT in the kwarg `cmap=CPT` with a range sufficient to transform the `vals` in colors. As an alternative to the above, provide a `makecpt` type `range` numeric vector to create a CPT. If none of these are provided a default `CPT = makecpt(range=(0,255,1))` will be used.
