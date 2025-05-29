```
TImodel1(params::Sleipnir.Parameters; DDF::F = 7.0/1000.0, acc_factor::F = 1.0/1000.0) where {F <: AbstractFloat}
```

与えられたパラメータを使用して、1つの度日係数（DDF）を持つ温度指数モデルを作成します。

# 引数

  * `params::Sleipnir.Parameters`: シミュレーションパラメータ。
  * `DDF::F`: 度日係数（デフォルトは7.0/1000.0）。
  * `acc_factor::F`: 蓄積係数（デフォルトは1.0/1000.0）。

# 戻り値

  * `TI1_model`: 指定されたパラメータを持つTImodel1のインスタンス。
