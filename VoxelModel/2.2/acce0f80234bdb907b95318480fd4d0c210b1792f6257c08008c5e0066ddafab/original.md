assign_voxel(grid::Array{Int, 3}, dl::Vector{<:Real}=[1.0, 1.0, 1.0], start::Vector{<:Real}=[0, 0, 0])

```
Assign grid to voxel space.

# Arguments
- `grid::Array{Int, 3}`: Interger grid array.
- `dl::Vector{<:Real}=[1.0, 1.0, 1.0]`: grid spacings.
- `start::Vector{<:Real}=[shift[] * 0.5, shift[] * 0.5, shift[] * 0.5]`: start point.
```
