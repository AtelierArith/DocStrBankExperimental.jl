```
OneSidedBootstrapLimit{T} <: BootstrapLimit{T}
```

定常な誤警報率を持つ片側ブートストラップ限界。

# フィールド

  * `sim::Vector{T}`: シミュレーションされた統計量のベクター。
  * `h::T`: 制御限界の現在の値。
  * `upw::Bool`: 制御限界が上限か下限かを示す。

# コンストラクタ

  * `OneSidedBootstrapLimit(S::AbstractStatistic, upw, B::Int)`: 新しい `OneSidedBootstrapLimit` オブジェクトを作成します。引数 `S` は `AbstractStatistic` オブジェクトです。引数 `upw` はブートストラップが片側で上側尾か下側尾かを決定します。引数 `B` はブートストラップの複製数を示す整数です。
