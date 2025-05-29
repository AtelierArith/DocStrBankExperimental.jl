```
TriMesh(name::String)
```

  * `name::String`: Name
  * `ncells::Int`: No. of cells
  * `normals::Vector{Vector{Float64}}`: Vector of normals for each cell
  * `zeroBased::Vector{Bool}`: If true, indices in connectivity information have zero-based indexing. A vector to make it mutable.
  * `points::Vector{Vector{Float64}}`: Vector of unique points
  * `cells::Vector{Vector{Int}}`: Vector of vertices for each cell as indices of `points`
