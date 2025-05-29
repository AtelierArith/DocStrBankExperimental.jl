```
open_parenthesis!(graph::G; map::Dict{Int,G}=Dict{Int,G}()) where {G<:AbstractGraph}

Recursively open parenthesis of subgraphs within the given graph `g`with in place form.  The graph eventually becomes 
a single Sum root node with multiple subgraphs that represents multi-product of nodes (not flattened).
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
  * `map::Dict{Int,G}=Dict{Int,G}()`: A dictionary that maps the id of an original node with its corresponding new node after transformation.

In recursive transform, nodes can be visited several times by different parents. This map keeps track of those visited, and reuse those transformed sub-branches instead of recreating them. parents
