```
struct Mesh3{VC, VI, VF<:AbstractArray{<:Face3D}, VB, VN, SV3, UR} <: AbstractMesh
    cells::VC           # vector of cells
    cell_nodes::VI      # vector of indices to access cell nodes
    cell_faces::VI      # vector of indices to access cell faces
    cell_neighbours::VI # vector of indices to access cell neighbours
    cell_nsign::VI      # vector of indices to with face normal correction (1 or -1 )
    faces::VF           # vector of faces
    face_nodes::VI      # vector of indices to access face nodes
    boundaries::VB      # vector of boundaries
    nodes::VN           # vector of nodes
    node_cells::VI      # vector of indices to access node cells
    get_float::SV3      # store mesh float type
    get_int::UR         # store mesh integer type
    boundary_cellsID::VI # vector of indices of boundary cell IDs
end
```
