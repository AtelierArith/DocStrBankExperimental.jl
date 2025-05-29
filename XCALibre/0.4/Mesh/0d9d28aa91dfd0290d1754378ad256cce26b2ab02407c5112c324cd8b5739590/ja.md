```
struct Cell{F<:AbstractFloat, SV3<:SVector{3,F},UR<:UnitRange{<:Integer}}
    centre::SV3     # セル重心の座標
    volume::F       # セルの体積
    nodes_range::UR # Mesh3.cell_nodes内のセルノードにアクセスするための範囲
    faces_range::UR # セルの面情報（面、隣接セルなど）にアクセスするための範囲
end
```
