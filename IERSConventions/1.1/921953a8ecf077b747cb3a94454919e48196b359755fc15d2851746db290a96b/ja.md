```
iers_rot3_itrf_to_pef(tt_s::Number, m::IERSModel=iers2010b)
```

国際地球参照フレーム（ITRF）から擬似地球固定（PEF）への回転行列を、`tt_s`の時刻において計算します。`tt_s`はJ2000からのTT秒で表現されています。

!!! note
    [`CPNd`](@ref)モデルは極運動の影響を無視するため、単位行列を返します。# TODO: 大きさを指定してください！


## 参照

[`iers_rot3_gcrf_to_pef`](@ref)も参照してください。
