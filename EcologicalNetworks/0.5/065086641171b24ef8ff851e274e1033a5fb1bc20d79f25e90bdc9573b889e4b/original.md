All networks in the package belong to the `AbstractEcologicalNetwork` type. They all have a field `A` to represent interactions as a *matrix*, and a number of fields for species. See the documentation for `AbstractBipartiteNetwork` and `AbstractUnipartiteNetwork`, as well as `AllowedSpeciesTypes` for the allowed types for species.

Note that *all* species in a network (including both levels of a bipartite network) *must* have the same type. For example, `["a", :b, "c"]` is not a valid array of species, as not all its elements have the same type.
