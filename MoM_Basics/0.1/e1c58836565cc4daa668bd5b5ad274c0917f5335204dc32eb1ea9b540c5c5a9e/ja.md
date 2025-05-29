```
MagneticDipole{FT<: Real}<:AntennaType
```

磁偶極子アンテナタイプ。

```
id      ::Integer               番号
Iml     ::Complex{FT}           磁流線値
V       ::FT                    磁流線振幅
phase   ::FT                    位相
orient  ::MVec3D{FT}            指向オイラー角
centerlc::MVec3D{FT}            ローカル座標での中心位置
centergb::MVec3D{FT}            グローバル座標での中心位置
l2gRot  ::MMatrix{3, 3, FT, 9}  ローカル座標からグローバル座標への回転変換行列
```
