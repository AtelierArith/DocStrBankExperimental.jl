```
struct Face3D{
    F<:AbstractFloat, 
    SV2<:SVector{2,<:Integer},
    SV3<:SVector{3,F}, 
    UR<:UnitRange{<:Integer}
    }
    
    nodes_range::UR # range to access face nodes in Mesh3.face_nodes
    ownerCells::SV2 # IDs of face owner cells (always 2)
    centre::SV3     # coordinates of face centre
    normal::SV3     # face normal unit vector
    e::SV3          # unit vector in the direction between owner cells
    area::F         # face area
    delta::F        # distance between owner cells centres
    weight::F       # linear interpolation weight
end
```
