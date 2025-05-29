```
Gb_Su(Tair,pressure,ustar; wind_zh, Dl, fc, N=2, Cd=0.2, hs=0.01, constants)
Gb_Su!(df; wind_zh, Dl, fc=nothing, N=2, Cd=0.2, hs=0.01, LAI, constants)
```

Su et al. 2001 に従った物理的に基づく定式化を使用して、熱移動に対する境界層導電率を推定します。

# 引数

  * `Tair`      : 空気温度 (℃)
  * `pressure`  : 大気圧 (kPa)
  * `ustar`     : 摩擦速度 (m s-1)
  * `df`        : 上記の変数を含む DataFrame または行列
  * `Dl`        : 葉の特性寸法 (m)
  * `fc`        : 植生被覆率 (0-1)、提供されていない場合は LAI から計算されます
  * `LAI`       : 一側葉面積指数 (-) - `fc` の代替。
  * `N`         : 熱交換に参加する葉の側面の数 (デフォルトは 2)
  * `Cd`        : 葉の抗力係数 (-)
  * `hs`        : 土壌の粗さ高さ (m)
  * `constants=`[`BigleafConstants`](@ref)`()`

# 値

[`compute_Gb!`](@ref) を参照

# 詳細

この定式化は、Massman 1999 によって開発された kB^(-1) モデルに基づいています。 Su et al. 2001 は次の近似を導出しました：

$$
k_{B1} = (k C_d f_c^2) / (4C_t u^*/u(z_h)) + k_{Bs-1}(1 - f_c)^2
$$

$$
f_c
$$

(植生被覆率) が欠けている場合、LAI から推定されます：$f_c = 1 - e^{-LAI/2}$

キャノピーの頂部での風速は、関数 [`wind_profile`](@ref) を使用して計算されます。

Ct は葉の熱伝達係数です (Massman 1999):

$$
C_t = P_r^{-2/3} R_{eh}^{-1/2}  N
$$

ここで、$P_r$ はプラントル数 (0.71 に設定)、$R_{eh}$ は葉のレイノルズ数です：

$$
R_{eh} = D_l \, wind(z_h) / v
$$

k*{Bs-1}、裸土表面の k*{B-1} 値は、Su et al. 2001 に従って計算されます：

$$
k_{Bs-1} = 2.46(Re)^{0.25} - ln(7.4)
$$

# 参考文献

  * Su, Z., Schmugge, T., Kustas, W. & Massman, W., 2001: An evaluation of two models for estimation of the roughness height for heat transfer between the land surface and the atmosphere. Journal of Applied Meteorology 40, 1933-1951.
  * Massman, W., 1999: A model study of kB H- 1 for vegetated surfaces using localized near-field' Lagrangian theory. Journal of Hydrology 223, 27-43.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987:  A preliminary multiple resistance routine for deriving dry deposition velocities from measured quantities. Water, Air, and Soil Pollution 36, 311-330.

```jldoctest; output = false
using DataFrames
df = DataFrame(
  Tair=25.0,pressure=100.0,wind=[3.0,4,5],ustar=[0.5,0.6,0.65],H=[200.0,230,250])
zh = 25; zr = 40
z0m = roughness_parameters(
  Roughness_wind_profile(), df.ustar, df.wind, df.Tair, df.pressure, df.H; zh, zr).z0m 
wind_zh = wind_profile(zh, df, 0.7*zh, z0m)
compute_Gb!(df,Su2001(); wind_zh, Dl=0.01, LAI=5)
# 同じ気象条件ですが、葉が大きい
compute_Gb!(df,Su2001(); wind_zh, Dl=0.1,LAI=5)
# 同じ条件、大きな葉、疎なキャノピー被覆 (LAI = 1.5)
compute_Gb!(df,Su2001(); wind_zh, Dl=0.1,LAI=1.5)
≈(df.Gb_h[1], 0.0638, rtol=1e-3)
# 出力
true
```
