```
plot_genealogy(genealogy[, ω]; kwargs...)
```

Plot a genealogy.

Only edges and vertices ancestral for `ω` are plotted.

Implemented as an extension to `Moonshine.jl`. To use this method, you have to import [`GraphMakie`](@ref) (and a [Makie](https://github.com/MakieOrg/Makie.jl) backend).

See also [`plot_layout`](@ref).

# Arguments

  * `wild_color` (`:blue`): color of wild vertices, that is those having only wild markers in `ω`.
  * `derived_color` (`:red`): color of derived (non-wild) vertices
  * `arrow_show` (`false`): whether or not to draw arrows
  * `edge_color` (`:gray`): color of edges
  * `edge_width` (`3`): width of edges
  * `layout` (`plot_layout(genealogy)`): layout function
  * `attributes...`: attributes passed directly to [`GraphMakie.graphplot`](@extref)
