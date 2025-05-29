```
sourceEfield(md::MagneticDipole{FT}, r_observe::Vec3D{FT};  r_coortype::Symbol=:C) where {FT<:Real}
```

計算磁気双極子 `md` がグローバル座標系で与えられた位置 `rvec` における電場。
