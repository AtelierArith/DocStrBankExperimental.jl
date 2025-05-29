```
MagneticDipole{FT<: Real}<:AntennaType
```

磁偶极子天线类型。

```
id      ::Integer               编号
Iml     ::Complex{FT}           磁流线值
V       ::FT                    磁流线幅值
phase   ::FT                    相位
orient  ::MVec3D{FT}            指向欧拉角
centerlc::MVec3D{FT}            局部坐标下的中心位置
centergb::MVec3D{FT}            全局坐标下的中心位置
l2gRot  ::MMatrix{3, 3, FT, 9}  局部坐标到全局坐标的旋转变换矩阵
```
