```
    MagneticDipole{FT}(
    id      ::Int32         =   zero(Int32);        # 番号
    Iml     ::CT            =   zero(CT),           # 磁流線値
    phase   ::FT            =   zero(FT),           # 位相（入力弧度(rad)単位）
    orient  ::MVec3D{FT}    =   zero(MVec3D{FT}),   # 指向オイラー角
    centerlc::MVec3D{FT}    =   zero(MVec3D{FT}),   # 局所座標下の中心位置
    centergb::MVec3D{FT}    =   zero(MVec3D{FT}),   # 全局座標下の中心位置
    I0S     ::FT            =   zero(FT),           # 電流環振幅
    unit                    =   :rad    ) 
    where{FT <: Real, CT <: Complex{FT}}
```
