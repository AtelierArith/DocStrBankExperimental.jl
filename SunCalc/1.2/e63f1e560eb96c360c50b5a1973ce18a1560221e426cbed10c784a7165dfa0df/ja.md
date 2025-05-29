```
getSunPosition(
    time::Union{DateTime,ZonedDateTime}
    lat::Real,
    lon::Real;
    keep=[:altitude, :azimuth])
```

指定された時間と場所の太陽の位置を計算します。`NamedTuple`または`DataFrame`を返します。

利用可能な変数:

| 変数         | 説明                                            |
|:---------- |:--------------------------------------------- |
| `altitude` | 地平線上の太陽の高度（ラジアン）、例えば地平線で0、天頂（頭上真上）でπ/2です。     |
| `azimuth`  | 地平線上の太陽の方位（南から西に測定された方向）、例えば0が南、π * 3/4が北西です。 |

# 例

```julia
using Dates, SunCalc
getSunPosition(DateTime(2000, 07, 01, 12, 00, 00), 54, 9)

getSunPosition(now(), 54, 9; keep=[:altitude])
```
