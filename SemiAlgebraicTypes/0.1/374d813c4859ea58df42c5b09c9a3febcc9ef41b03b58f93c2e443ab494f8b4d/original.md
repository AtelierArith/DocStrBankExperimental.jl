```
Mesh{T}
```

Mesh corresponding to an array of points (`Vector{T}`), an array of edges (`Vector{Int64}`) and an array of faces (`Vector{Int64}`).

## Example

```jldoctest
julia> mesh(Float64);

julia> mesh([[cos(i*pi/5), sin(i*pi/5), 0.0] for i in 1:10], Edge[], [[1,i,i+1] for i in 1:9]);
```

**Fields:**

  * `points  ::Matrix{T}`: array of points
  * `edges   ::Vector{Vector{Int64}}`: array of edges
  * `faces   ::Vector{Vector{Int64}}`: array of faces
  * `normals ::Matrix{T}`: array of normals
  * `attr    ::Dict{Symbol,Any}`: attributes
