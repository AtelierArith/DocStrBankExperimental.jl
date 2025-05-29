GraphProperties(diff::Diff)

Create the graph properties difference from a given [`Diff`](@ref). The graph's properties after applying the [`Diff`](@ref) will be `get_properties(graph) + GraphProperties(diff)`. For reverting a diff, it's `get_properties(graph) - GraphProperties(diff)`.
