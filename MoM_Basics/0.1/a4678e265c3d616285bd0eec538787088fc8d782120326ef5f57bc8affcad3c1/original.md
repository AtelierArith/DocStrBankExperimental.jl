```
sourceEfield(md::MagneticDipole{FT}, r_observe::Vec3D{FT};  r_coortype::Symbol=:C) where {FT<:Real}
```

计算磁偶极 `md` 在全局坐标下给定位置 `rvec` 处的电场。
