```
convert_s(::Type{V}, s, problem::Union{MDP,POMDP}) where V<:AbstractArray
convert_s(::Type{S}, vec::V, problem::Union{MDP,POMDP}) where {S,V<:AbstractArray}
```

Convert a state to vectorized form or vice versa.
