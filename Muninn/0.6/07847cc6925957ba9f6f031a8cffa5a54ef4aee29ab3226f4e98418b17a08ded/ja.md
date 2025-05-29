```
TImodel2(params::Parameters; DDF_snow::F = 3.0/1000.0, DDF_ice::F = 6.0/1000.0, acc_factor::F = 1.0/1000.0) where {F <: AbstractFloat}
```

質量収支計算のための二つの度日係数を持つ温度インデックスモデル（TImodel2）を作成します。

# 引数

  * `params::Parameters`: シミュレーション設定を含むパラメータオブジェクト。
  * `DDF_snow::F`: 雪の度日係数（デフォルト: 3.0/1000.0）。
  * `DDF_ice::F`: 氷の度日係数（デフォルト: 6.0/1000.0）。
  * `acc_factor::F`: 蓄積係数（デフォルト: 1.0/1000.0）。

# 戻り値

  * `TI2_model`: 指定されたパラメータを持つTImodel2のインスタンス。
