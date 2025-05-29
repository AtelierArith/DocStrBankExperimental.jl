```
getMoonIllumination(
    time::Union{Date,DateTime,ZonedDateTime};
    keep=[:fraction, :phase, :angle])
```

指定された時間の月の照明を計算します。`NamedTuple`または`DataFrame`を返します。

利用可能な変数:

| 変数         | 説明                                                                    |
|:---------- |:--------------------------------------------------------------------- |
| `fraction` | 月の照らされた部分の割合; 0.0（新月）から1.0（満月）まで変動します                                 |
| `phase`    | 月の位相; 0.0から1.0まで変動し、以下に説明されています                                       |
| `angle`    | 月の円盤の北点から東に向かって計算された照らされた部分の中間角度（ラジアン）; 角度が負の場合は月が満ちており、正の場合は月が欠けています |

月の位相値は次のように解釈されるべきです:

  * `0`: 新月
  * *満ち始めの三日月*
  * `0.25`: 上弦の月
  * *満ちた三日月*
  * `0.5`: 満月
  * *欠けた三日月*
  * `0.75`: 下弦の月
  * *欠け始めの三日月*

# 例

```julia
using Dates, SunCalc
getMoonIllumination(Date(2000, 07, 01))

getMoonIllumination(now(), keep=[:fraction])
```
