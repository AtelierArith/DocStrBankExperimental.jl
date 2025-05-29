Convert a free diagram to a bipartite free diagram.

Reduce a free diagram to a free bipartite diagram with the same limit (the default, `colimit=false`) or the same colimit (`colimit=true`). The reduction is essentially the same in both cases, except for the choice of where to put isolated vertices, where we follow the conventions described at [`cone_objects`](@ref) and [`cocone_objects`](@ref). The resulting object is a bipartite free diagram equipped with maps from the vertices of the bipartite diagram to the vertices of the original diagram.
