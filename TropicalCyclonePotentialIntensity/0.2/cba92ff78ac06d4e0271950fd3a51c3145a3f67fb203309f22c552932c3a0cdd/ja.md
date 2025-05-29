```
get_buoyancy_of_lifted_parcel(tparcel <: Real,rparcel <: Real,pparcel <: Real,t :: Array{<: Real},r :: Array{<: Real},p  :: Array{<: Real},ptop=50)
```

レベル `z` ごとに定義された浮力プロファイルを取得します。これは、レベル `p = pparcel` からレベル `p(z)` まで持ち上げられたパーセルの温度の差です。 `Buoyancy(z) = Tv_lifted(z) - Tv_env(z)` 

これは、パーセルを断熱的に持ち上げるべきかどうかを決定するために、持ち上げ凝結レベル (LCL) を計算します。断熱的でない場合は、特定のエントロピーを保持しながらレベルでの温度を見つけるためにニュートン-ラフソン法を使用します。 `Buoyancy(z) = Tv_lifted(z) - Tv_env(z)` 
