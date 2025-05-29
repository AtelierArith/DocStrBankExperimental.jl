```
function ref_add_core!(ref::Dict{Symbol,Any})
```

Returns a dict that stores commonly used pre-computed data obtained from the data dictionary, primarily for converting data-types, filtering out loads in the transmission-side system, removing slack generators in the distribution-side system, and storing system-wide values that need to be computed globally. Some of the common keys include:

  * `See ref_add_core!(ref) from PowerModels`),
  * `See ref_add_core!(ref) from PowerModelsDistribution`),
  * `:boundary` – the set of boundary elements that are active in the network,
  * `:arcs_boundary_from` – the set `[(i,b["f_bus"],b["t_bus"]) for (i,b) in ref[:boundary]]`,
  * `:arcs_boundary_to` – the set `[(i,b["t_bus"],b["f_bus"]) for (i,b) in ref[:boundary]]`,
  * `:arcs_boundary` – the set of arcs from both `arcs_boundary_from` and `arcs_boundary_to`,
  * `:bus_arcs_boundary_from` – the mapping `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs_boundary_from]])`,
  * `:bus_arcs_boundary_to` – the mapping `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs_boundary_to]])`.
