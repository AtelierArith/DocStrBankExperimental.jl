```
localObs2GlobalObs(r̂θϕs_obs::Matrix{r̂θϕInfo{FT}}, l2gRot::StaticMatrix{3,3, FT}) where {FT}
```

局所観測空間の角度情報 `r̂θϕs_obs` に基づいて、与えられた局所からグローバル座標への回転行列 `l2gRot` の下でのグローバル座標の観測空間の角度情報を計算します。
