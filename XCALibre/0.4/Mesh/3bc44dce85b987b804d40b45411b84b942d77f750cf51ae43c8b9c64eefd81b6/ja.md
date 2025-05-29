```
struct Face3D{
    F<:AbstractFloat, 
    SV2<:SVector{2,<:Integer},
    SV3<:SVector{3,F}, 
    UR<:UnitRange{<:Integer}
    }
    
    nodes_range::UR # メッシュの面ノードにアクセスするための範囲
    ownerCells::SV2 # 面の所有セルのID（常に2）
    centre::SV3     # 面の中心の座標
    normal::SV3     # 面の法線単位ベクトル
    e::SV3          # 所有セル間の方向の単位ベクトル
    area::F         # 面の面積
    delta::F        # 所有セルの中心間の距離
    weight::F       # 線形補間の重み
end
```
