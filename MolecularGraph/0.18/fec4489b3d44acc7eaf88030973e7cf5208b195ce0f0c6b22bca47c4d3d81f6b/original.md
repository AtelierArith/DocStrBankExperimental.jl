```
VF2Matcher{T,U,G<:SimpleGraph{T},H<:SimpleGraph{U}}
```

Lazy iterator that generate all isomorphism mappings between `G` and `H`.

`matchtype` should be one of the followings

  * `:isomorphic`: G is isomorphic to H
  * `:subgraph_isomorphic`: a node-induced subgraph of G is isomorphic to H
  * `:monomorphic`: a subgraph of G is monomorphic to H

# Options

  * `vmatch::Function`: a function for semantic node attribute matching (default: (a, b) -> true)
  * `ematch::Function`: a function for semantic edge attribute matching (default: (a, b) -> true)
  * `mandatory::Dict{Int,Int}`: mandatory node mapping (if matchtype=:edgeinduced, edge mapping)
  * `forbidden::Dict{Int,Int}`: forbidden node mapping (if matchtype=:edgeinduced, edge mapping)
  * `timeout::Union{Int,Nothing}`: if specified, abort vf2 calculation when the time reached and return empty iterator (default: 10 seconds)
