```
sourceLocalEfield(md::MagneticDipole{FT}, r_observe::Vec3D{FT};  r_coortype::Symbol=:C) where {FT<:Real}
```

計算磁偶極 `md` 在磁偶極局部座標給定位置 `rvec` 處的電場。
