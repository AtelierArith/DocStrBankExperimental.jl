```
globalObs2LocalObs(r̂θϕs_obs::Matrix{r̂θϕInfo{FT}}, l2gRot::StaticMatrix{3,3, FT}) where {FT}
```

根据全局观测空间角度信息 `r̂θϕs_obs` 计算给定局部至全局坐标旋转矩阵 `l2gRot` 下局部坐标的观测空间角度信息。
