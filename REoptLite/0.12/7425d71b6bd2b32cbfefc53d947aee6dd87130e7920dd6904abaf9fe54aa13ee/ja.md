```
simulate_outages(;batt_kwh=0, batt_kw=0, pv_kw_ac_hourly=[], init_soc=[], critical_loads_kw=[], 
    wind_kw_ac_hourly=[], batt_roundtrip_efficiency=0.829, diesel_kw=0, fuel_available=0, b=0, m=0, 
    diesel_min_turndown=0.3
)
```

年の各時間ステップで開始する停電の時系列シミュレーション。各停電で重要な負荷がどれだけの時間ステップで満たされるかを計算するために使用され、これにより重要な負荷を満たす確率が決定されます。

# 引数

  * `batt_kwh`: float, バッテリーの蓄電容量
  * `batt_kw`: float, バッテリーインバータの容量
  * `pv_kw_ac_hourly`: floatのリスト, PVシステムのAC生産
  * `init_soc`: 0から1の間のfloatのリスト, 初期充電状態
  * `critical_loads_kw`: floatのリスト
  * `wind_kw_ac_hourly`: floatのリスト, 風力タービンのAC生産
  * `batt_roundtrip_efficiency`: バッテリーの往復効率
  * `diesel_kw`: float, ディーゼル発電機の容量
  * `fuel_available`: float, 利用可能なディーゼル燃料のガロン数
  * `b`: float, ディーゼル燃料の燃焼率の切片係数 (y = m*x + b*rated_capacity)  [gal/kwh/kw]
  * `m`: float, ディーゼル燃料の燃焼率の傾き (y = m*x + b*rated_capacity)  [gal/kWh]
  * `diesel_min_turndown`: 発電機容量の最小ターニングダウンの割合 (0から1)

辞書を返します

```
    "resilience_by_timestep": 各時間ステップで開始する停電に対して重要な負荷が満たされる時間ステップのベクトル,
    "resilience_hours_min": "resilience_by_timestep"の最小値,
    "resilience_hours_max": "resilience_by_timestep"の最大値,
    "resilience_hours_avg": "resilience_by_timestep"の平均値,
    "outage_durations": 生存の確率がゼロでない停電の持続時間の整数のベクトル,
    "probs_of_surviving": "outage_durations"に対応する確率のベクトル,
    "probs_of_surviving_by_month": 月単位で計算された確率のベクトル,
    "probs_of_surviving_by_hour_of_the_day": 時間単位で計算された確率のベクトル,
}
```
