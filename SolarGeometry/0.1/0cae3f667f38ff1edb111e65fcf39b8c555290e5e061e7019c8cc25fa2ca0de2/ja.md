```
function solar_azimuth_altitude(Δt, start_time::DateTime, lat, lon, alt)
```

与えられたUTC時間`start_time`、緯度`lat`、経度`lon`、高度`alt`およびオフセット`Δt`に対して、`start_time + Δt`でのその位置に対する太陽の方位角と太陽の高度角（度単位）を返します。このバージョンの関数は、DateTimeが無限精度の秒を許可しないため、ユーザーが連続的な出力を生成できるようにするためのものです。
