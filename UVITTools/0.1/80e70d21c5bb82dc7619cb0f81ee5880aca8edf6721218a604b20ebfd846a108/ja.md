```
fuv_grating2_ea(lamA[,order = -2])
```

指定した波長（オングストローム）と回折格子の次数 -1 または -2 における FUV-Grating2 有効面積を cm^2 で計算します。

有効面積の計算は、[Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract) で行われた回折格子のキャリブレーションに基づいています。この関数はカウントスペクトルのフラックスキャリブレーションに使用されます。

...

# 引数

## 必須

  * `lam::Number`: 波長（オングストローム）。

## オプション

-`order::Int`: 回折格子の次数 -1 または -2。 ...

# 例

```jldoctest
julia> fuv_grating2_ea(1450.4,order=-2)
4.076758827954109
```
