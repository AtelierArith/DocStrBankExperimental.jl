```
struct Cell{F<:AbstractFloat, SV3<:SVector{3,F},UR<:UnitRange{<:Integer}}
    centre::SV3     # coordinate of cell centroid
    volume::F       # cell volume
    nodes_range::UR # range to access cell nodes in Mesh3.cell_nodes
    faces_range::UR # range to access cell faces info (faces, neighbours cells, etc.)
end
```
