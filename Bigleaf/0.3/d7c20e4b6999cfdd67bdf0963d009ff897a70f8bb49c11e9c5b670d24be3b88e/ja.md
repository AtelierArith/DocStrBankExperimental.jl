```
calc_sun_position_hor(datetime, lat, long)
```

与えられた時間と観測者の座標における太陽の位置を水平座標で計算します。

# 引数:

  * `datetime`: 時間: `ZonedDateTime` または UTC と仮定される `DateTime`
  * `lat`, `long`: 緯度と経度（度単位）

# 値

`NamedTuple`: `lat` と `long` と同じ型のエントリを持つ太陽の位置

  * `altitude`: 地平線上の角度 [rad]。
  * `azimuth`: 北の東側の地平面に対する角度 [rad]
  * `hourangle`: [rad] AstroLib.eq2hor によって出力される。太陽の正午以降の時間 [day/2pi] を表すようです。ローカルタイムの正午での値は (ローカル時間 - 太陽時間) を提供します。
