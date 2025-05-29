```
PlaneWave{FT<:Real}<:ExcitingSource
```

平面波源：

```
θ   ::FT            球坐标角度θ
ϕ   ::FT            球坐标角度ϕ
α   ::FT            波极化方向相对于 θhat_source 绕K̂_v旋转的角度
f   ::FT            波频率
V   ::FT            波激励幅度
E_v ::SVec3D{FT}    入射波电场极化矢量
k̂   ::SVec3D{FT}    入射波波矢向量
```

默认构造函数：

```julia
PlaneWave{FT}(θ::FT, ϕ::FT, α::FT, V::FT = one(FT))
```
