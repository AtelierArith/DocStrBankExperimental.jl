```
@liquid name temp dens visc surftens pv Ev
```

指定された名前の液体を作成し、粘度 `visc`、表面張力 `surftens`、蒸気圧 `pv`、および体積弾性率 `Ev` を参照温度 `temp` で設定します。これらのうち、デフォルトでない場合は単位を指定する必要があります。

# 例

```jldoctest myliq
julia> @liquid MyWater 15u"°C" 999 1.13e-3 7.34e-2 1.77e3 2.15e9

julia> MyWater
Liquid with
   Density = 999.0 kg m⁻³
   Viscosity = 0.00113 kg m⁻¹ s⁻¹
   Kinematic viscosity = 1.131131131131131e-6 m² s⁻¹
   Specific weight = 9796.84335 N m⁻³
   Surface tension = 0.0734 N m⁻¹
   Bulk modulus = 2.15e9 Pa
   Vapor pressure = 1770.0 Pa
   at reference temp 288.15 K
```
