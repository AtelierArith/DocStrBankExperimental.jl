```
Norman_Longwave(ϵ=0.98, ϵ_g=1.0, T_veg=25, T_g=20, L_sky=400)

ノーマン（1979）によるキャノピーを通る長波放射の移動
```

# 引数

  * `ϵ`     : 葉のエミッシビティ
  * `ϵ_g`   : 地面（土壌）のエミッシビティ
  * `LAI`   : 葉面積指数 (m2/m2)
  * `L_sky` : 大気の長波放射 (W/m2)

# 例

```julia
n = 50
ϵ = [1.0; fill(0.98, n - 1)]
T_leaf = [20.0; fill(25.0, n - 1)]
τd = ones(n) .* 0.915     # 各葉層を通る拡散放射の透過率
L_up, L_dn, Rln, Rln_soil, Rln_veg = Norman_Longwave(T_leaf, ϵ, τd)

# irup  = 447.16643
# irveg = -75.54891
# irsoi =  28.38247
```
