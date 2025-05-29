均一冷却はPauliusとGarner（2006年）に従い、デフォルトの温度傾向を-1.5K/日（`time_scale`が16時間の場合は1K/16時間）として、成層圏（`temp < temp_min`として診断される）を除くすべてのレベルに適用され、成層圏の`temp_stratosphere`に向かう緩和項が`time_scale_stratosphere`で適用されます。

```
dT/dt = -1.5K/day for T > 207.5K else (200K-T) / 5 days
```

フィールドは次のとおりです。

  * `time_scale::Dates.Second`: [OPTION] 冷却の時間スケール、デフォルト = -1.5K/日 = -1K/16時間
  * `temp_min::Any`: [OPTION] 成層圏の緩和が適用される温度 [K]
  * `temp_stratosphere::Any`: [OPTION] 成層圏の緩和の目標温度 [K]
  * `time_scale_stratosphere::Dates.Second`: [OPTION] 成層圏の緩和の時間スケール
