```
struct Node{SV3<:SVector{3,<:AbstractFloat}, UR<:UnitRange{<:Integer}}
    coords::SV3     # node coordinates
    cells_range::UR # range to access neighbour cells in Mesh3.node_cells
end
```
