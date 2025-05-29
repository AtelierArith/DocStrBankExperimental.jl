Define OSMPlot plotting function with some attribute defaults.

## Arguments

`osm::LightOSM.OSMGraph`

## Keyword arguments

`graphplotkwargs::NamedTuple = (; )` : All kwargs are passed on to `GraphMakie.graphplot!`.      All kwargs that work with graphplot will also work here (see [GraphMakie docs](https://juliaplots.org/GraphMakie.jl/stable/#The-graphplot-Recipe) for reference).     Extending the defaults can be done by providing `graphplotkwargs = (; kwargs...)`. `hide_elabels::Bool = false` : Show or hide edge labels. `hide_nlabels::Bool = true` : Show or hide node labels. `buildings::Union{Dict{Integer, LightOSM.Building}, Nothing} = nothing` : Buildings polygons     are plotted if this is not nothing. `buildingskwargs::NamedTuple = (; )` : All kwargs are passed on to `Makie.poly` and will     overwrite the default plotting behaviour `inspect_nodes::Bool = false` : Enables/disables inspection of OpenStreetMap nodes. `inspect_edges::Bool = true` : Enables/disables inspection of OpenStreetMap ways.
