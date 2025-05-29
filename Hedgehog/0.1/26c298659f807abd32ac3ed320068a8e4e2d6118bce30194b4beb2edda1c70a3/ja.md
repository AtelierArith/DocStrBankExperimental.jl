```
VanillaOption{TS,TE,E,C,U} <: AbstractPayoff
```

指定された行使スタイル、コール/プットタイプ、および基礎となるタイプを持つバニラオプション。

# フィールド

  * `strike`: オプションの行使価格。
  * `expiry`: 内部ティック単位での満期（成熟）時間。
  * `exercise_style`: `European` または `American` のインスタンス。
  * `call_put`: `Call` または `Put` のインスタンス。
  * `underlying`: `Spot` または `Forward` のいずれか。
