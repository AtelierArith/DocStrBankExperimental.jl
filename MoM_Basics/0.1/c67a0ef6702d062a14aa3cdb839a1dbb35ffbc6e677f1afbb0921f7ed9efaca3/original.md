```
    MagneticDipole{FT}(
    id      ::Int32         =   zero(Int32);        # 编号
    Iml     ::CT            =   zero(CT),           # 磁流线值
    phase   ::FT            =   zero(FT),           # 相位（输入弧度(rad)单位）
    orient  ::MVec3D{FT}    =   zero(MVec3D{FT}),   # 指向欧拉角
    centerlc::MVec3D{FT}    =   zero(MVec3D{FT}),   # 局部坐标下的中心位置
    centergb::MVec3D{FT}    =   zero(MVec3D{FT}),   # 全局坐标下的中心位置
    I0S     ::FT            =   zero(FT),           # 电流环幅值
    unit                    =   :rad    ) 
    where{FT <: Real, CT <: Complex{FT}}
```
