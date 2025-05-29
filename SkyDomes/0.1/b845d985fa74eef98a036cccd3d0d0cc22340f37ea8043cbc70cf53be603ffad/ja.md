```
waveband_conversion(;Itype = :direct, waveband = :PAR, mode = :power)
```

太陽放射（W/m2）から特定の波長帯への変換係数を返します。出力は、パワー（W/m2）または光子フラックス（umol/m2/s）のいずれかです。係数は、オランダ（緯度52°N）の6月21日の晴天時のBirdスペクトルモデルに基づいています。

# 引数

  * `Itype`: 太陽放射のタイプ、`:direct`または`:diffuse`のいずれか。
  * `waveband`: 興味のある波長帯、`:PAR`、`:UV`、`:blue`、`:red`、`:green`、または`:NIR`のいずれか。
  * `mode`: 対象の物理単位、`:power`（W/m^2）または`:flux`（umol/m^2/s）のいずれか。

# 例

```julia
waveband_conversion(Itype = :diffuse, waveband = :UV, mode = :flux)
waveband_conversion(waveband = :NIR)
```
