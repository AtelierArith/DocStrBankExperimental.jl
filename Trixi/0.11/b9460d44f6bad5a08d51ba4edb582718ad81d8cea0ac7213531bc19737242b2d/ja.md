```
ControllerThreeLevel(semi, indicator; base_level=1,
                                      med_level=base_level, med_threshold=0.0,
                                      max_level=base_level, max_threshold=1.0)
```

三レベルに基づくAMRコントローラー（優先順位の降順）：

  * `indicator > max_threshold` の場合、ターゲットレベルを `max_level` に設定します
  * `indicator > med_threshold` の場合、ターゲットレベルを `med_level` に設定します；もし `med_level < 0` の場合、ターゲットレベルを現在のレベルに設定します
  * それ以外の場合、ターゲットレベルを `base_level` に設定します
