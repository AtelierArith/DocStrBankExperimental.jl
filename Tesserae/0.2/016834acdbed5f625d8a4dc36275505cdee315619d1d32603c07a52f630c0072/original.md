```
generate_grid(GridProp, mesh)
```

Generate a background grid where each element is of type `GridProp`. The first field of `GridProp` is designated for `mesh`, and thus its type must match `eltype(mesh)`. The resulting grid is a [`StructArray`](https://github.com/JuliaArrays/StructArrays.jl).

# Examples

```jldoctest
julia> struct GridProp{dim, T}
           x  :: Vec{dim, T}
           m  :: Float64
           mv :: Vec{dim, T}
           f  :: Vec{dim, T}
           v  :: Vec{dim, T}
           vⁿ :: Vec{dim, T}
       end

julia> grid = generate_grid(GridProp{2, Float64}, CartesianMesh(0.5, (0,3), (0,2)));

julia> grid[1]
GridProp{2, Float64}([0.0, 0.0], 0.0, [0.0, 0.0], [0.0, 0.0], [0.0, 0.0], [0.0, 0.0])

julia> grid.x
7×5 CartesianMesh{2, Float64, Vector{Float64}}:
 [0.0, 0.0]  [0.0, 0.5]  [0.0, 1.0]  [0.0, 1.5]  [0.0, 2.0]
 [0.5, 0.0]  [0.5, 0.5]  [0.5, 1.0]  [0.5, 1.5]  [0.5, 2.0]
 [1.0, 0.0]  [1.0, 0.5]  [1.0, 1.0]  [1.0, 1.5]  [1.0, 2.0]
 [1.5, 0.0]  [1.5, 0.5]  [1.5, 1.0]  [1.5, 1.5]  [1.5, 2.0]
 [2.0, 0.0]  [2.0, 0.5]  [2.0, 1.0]  [2.0, 1.5]  [2.0, 2.0]
 [2.5, 0.0]  [2.5, 0.5]  [2.5, 1.0]  [2.5, 1.5]  [2.5, 2.0]
 [3.0, 0.0]  [3.0, 0.5]  [3.0, 1.0]  [3.0, 1.5]  [3.0, 2.0]

julia> grid.v
7×5 Matrix{Vec{2, Float64}}:
 [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]
 [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]
 [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]
 [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]
 [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]
 [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]
 [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]  [0.0, 0.0]
```
