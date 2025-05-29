```
kinematic_viscosity(Tair,pressure; ...)
```

空気の運動粘度を計算します。

# パラメータ

  * Tair      空気温度 (℃)
  * pressure  大気圧 (kPa)

オプション 

  * `constants=`[`BigleafConstants`](@ref)`()`: Kelvin, pressure0, Tair0, kPa2Pa のエントリを持つ辞書

# 詳細

v は空気の運動粘度 (m2 s-1) であり、(Massman 1999b) によって次のように与えられます：

$$
v = 1.327 * 10^-5(pressure0/pressure)(Tair/Tair0)^{1.81}
$$

# 値

空気の運動粘度 (m2 s-1)

# 参考文献

Massman, W.J., 1999b: Hg蒸気の分子拡散率、O2およびN2のSTP近傍、ならびにSTP近傍の空気の運動粘度および熱拡散率。大気環境 33, 453-457。      

# 例

```jldoctest; output = false
Tair,pressure = 25.0,100.0
vis = kinematic_viscosity(Tair,pressure)
≈(vis, 1.58e-5, atol =1e-7)
# output
true
```
