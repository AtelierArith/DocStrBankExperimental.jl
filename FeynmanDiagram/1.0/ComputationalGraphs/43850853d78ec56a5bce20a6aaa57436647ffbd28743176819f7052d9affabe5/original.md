```
flatten_sum!(graph::G; map::Dict{Int,G}=Dict{Int,G}()) where {G<:AbstractGraph}

Recursively merge multi-product sub-branches within the given graph `g  by merging  sum subgraphs 
into their parent sum graphs in the in-place form.
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
  * `map::Dict{Int,G}=Dict{Int,G}()`: A dictionary that maps the id of an original node with its corresponding new node after transformation.

In recursive transform, nodes can be visited several times by different parents. This map keeps track of those visited, and reuse those transformed sub-branches instead of recreating them.
