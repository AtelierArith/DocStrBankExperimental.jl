```
ControllerThreeLevelCombined(semi, indicator_primary, indicator_secondary;
                             base_level=1,
                             med_level=base_level, med_threshold=0.0,
                             max_level=base_level, max_threshold=1.0,
                             max_threshold_secondary=1.0)
```

三レベルに基づくAMRコントローラー（優先順位の降順）：

  * `indicator_primary > max_threshold` の場合、ターゲットレベルを `max_level` に設定します
  * `indicator_primary > med_threshold` の場合、ターゲットレベルを `med_level` に設定します；もし `med_level < 0` の場合、ターゲットレベルを現在のレベルに設定します
  * それ以外の場合、ターゲットレベルを `base_level` に設定します

`indicator_secondary >= max_threshold_secondary` の場合、ターゲットレベルを `max_level` に設定します。
