```
path_from_parents(parents::P, goal::V, path_length::N) where {P <: Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}} where {U <: Integer, V <: Integer, N <: Integer}
```

Extracts shortest path given dijkstra parents of a given source, providing `path_length` allows preallocation of the array and avoids the need to reverse the path.

# Arguments

  * `parents::Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}`: Mapping of dijkstra parent states.
  * `goal::V`: Goal vertex.
  * `path_kength::N`: Known length of the return path, allows preallocation of final path array.

# Return

  * `Union{Nothing,Vector{U}}`: Array veritces represeting shortest path to `goal`.
