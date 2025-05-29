```
getMoonPosition(
    time::Union{DateTime,ZonedDateTime},
    lat::Real,
    lon::Real;
    keep=[:altitude, :azimuth, :distance, :parallacticAngle])
```

指定された時間と場所のために月の位置を計算します。`NamedTuple`または`DataFrame`を返します。

利用可能な変数:

| 変数                 | 説明              |
|:------------------ |:--------------- |
| `altitude`         | 地平線上の月の高度（ラジアン） |
| `azimuth`          | 月の方位（ラジアン）      |
| `distance`         | 月までの距離（キロメートル）  |
| `parallacticAngle` | 月の視差角（ラジアン）     |

# 例

```julia
using Dates, SunCalc
getMoonPosition(DateTime(2000, 07, 01, 12, 00, 00), 54, 9)

getMoonPosition(now(), 54, 9; keep=[:altitude])
```
