```
struct Node{SV3<:SVector{3,<:AbstractFloat}, UR<:UnitRange{<:Integer}}
    coords::SV3     # ノードの座標
    cells_range::UR # Mesh3.node_cells内の隣接セルにアクセスするための範囲
end
```
