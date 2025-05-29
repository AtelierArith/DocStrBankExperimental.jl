```
compute_MB(mb_model::TImodel1, climate_2D_period::Climate2Dstep)
```

与えられた質量バランスモデルと気候期間の質量バランス（MB）を計算します。

# 引数

  * `mb_model::TImodel1`: 蓄積係数（`acc_factor`）や度日係数（`DDF`）などのパラメータを含む質量バランスモデル。
  * `climate_2D_period::Climate2Dstep`: 雪の蓄積（`snow`）や正の度日（`PDD`）を含む特定の期間の気候データ。

# 戻り値

  * 蓄積係数と雪の積の差、および度日係数と正の度日の積の差として計算された質量バランスを表す数値配列。
