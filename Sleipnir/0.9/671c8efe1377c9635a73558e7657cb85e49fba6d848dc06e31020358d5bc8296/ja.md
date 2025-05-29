```
Climate2Dstep{F <: AbstractFloat}
```

さまざまな気候関連パラメータを持つ2D気候時間ステップを表す可変構造体です。

# キーワード引数

  * `temp::Matrix{F}`: 温度行列。
  * `PDD::Matrix{F}`: 正の度日行列。
  * `snow::Matrix{F}`: 降雪行列。
  * `rain::Matrix{F}`: 降雨行列。
  * `gradient::F`: 勾配値。
  * `avg_gradient::F`: 平均勾配値。
  * `x::Vector{F}`: X座標ベクトル。
  * `y::Vector{F}`: Y座標ベクトル。
  * `ref_hgt::F`: 参照高さ。
