```
path_from_parents(parents::P, goal::V) where {P <: Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}} where {U <: Integer, V <: Integer}
```

Extracts shortest path given dijkstra parents of a given source.

# Arguments

  * `parents::Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}`: Mapping of    dijkstra parent states.
  * `goal::V`: Goal vertex.

# Return

  * `Union{Nothing,Vector{U}}`: Array veritces represeting shortest path to `goal`.
