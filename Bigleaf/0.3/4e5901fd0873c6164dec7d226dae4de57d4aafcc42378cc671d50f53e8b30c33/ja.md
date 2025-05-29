```
potential_radiation(datetime, lat, long)
potential_radiation(doy, hour, lat, long; timezone,year)
```

指定された地理的位置と時間に対する潜在放射を計算します。

潜在放射は年によって変わらないため（特定の場所と日中および年の日に対して）、時間はdoyとhourで代わりに指定できます。

# 引数

  * datetime:  UTC タイムスタンプ。
  * lat:       緯度（小数度）
  * long:      経度（小数度）
  * doy:       年の日（1から始まる整数）
  * hour:      日内の時間（0.0 .. 24.0 浮動小数点）

オプション     

  * timezone:  doyとhourのためのタイムゾーン、指定された経度に最も近い "GMT+x" にデフォルト設定。
  * year: doyとhourのための特定の年
  * `...`: [`extraterrestrial_radiation`](@ref) に渡される他のキーワード引数（`constants`や`FT`など）

# 値

潜在放射のベクトル (W m-2)

# 例

```@example
# 指定された経度に最も近いGMT+xの時間を仮定
potrad = potential_radiation(160, 10.5, 51.0, 11.5)
```
