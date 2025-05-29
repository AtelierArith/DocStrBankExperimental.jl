```
convert_o(::Type{V}, o, problem::Union{MDP,POMDP}) where V<:AbstractArray
convert_o(::Type{O}, vec::V, problem::Union{MDP,POMDP}) where {O,V<:AbstractArray}
```

Convert an observation to vectorized form or vice versa.
