```
struct Mesh3{VC, VI, VF<:AbstractArray{<:Face3D}, VB, VN, SV3, UR} <: AbstractMesh
    cells::VC           # セルのベクター
    cell_nodes::VI      # セルノードにアクセスするためのインデックスのベクター
    cell_faces::VI      # セルフェイスにアクセスするためのインデックスのベクター
    cell_neighbours::VI # セルの隣接セルにアクセスするためのインデックスのベクター
    cell_nsign::VI      # フェイス法線補正のためのインデックスのベクター (1 または -1)
    faces::VF           # フェイスのベクター
    face_nodes::VI      # フェイスノードにアクセスするためのインデックスのベクター
    boundaries::VB      # 境界のベクター
    nodes::VN           # ノードのベクター
    node_cells::VI      # ノードセルにアクセスするためのインデックスのベクター
    get_float::SV3      # メッシュの浮動小数点型を格納
    get_int::UR         # メッシュの整数型を格納
    boundary_cellsID::VI # 境界セルIDのインデックスのベクター
end
```
