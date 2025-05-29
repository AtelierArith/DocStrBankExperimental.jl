```
VanillaOption(strike, expiry_date, exercise_style, call_put, underlying)
```

カレンダー `expiry_date`（例：`Date`、`DateTime` など）を使用して `VanillaOption` を構築します。これは内部的に `to_ticks` を介してティック単位に変換されます。

# 引数

  * `strike`: オプションの行使価格。
  * `expiry_date`: 日付/時間オブジェクトとしての満期（ティックに変換されます）。
  * `exercise_style`: `European()` または `American()`。
  * `call_put`: `Call()` または `Put()`。
  * `underlying`: `Spot()` または `Forward()`。

# 戻り値

  * 完全に構築された `VanillaOption` インスタンス。
