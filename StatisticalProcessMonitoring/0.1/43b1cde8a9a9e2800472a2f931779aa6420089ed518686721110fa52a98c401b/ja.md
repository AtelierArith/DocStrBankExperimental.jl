```
TwoSidedBootstrapLimit{T} <: BootstrapLimit{T}
```

定常な誤警報率を持つ両側ブートストラップ制限。

# フィールド

  * `sim::Vector{T}`: シミュレーションされた統計量のベクター。
  * `h::Vector{T}`: 制御限界の現在の値。

# コンストラクタ

  * `TwoSidedBootstrapLimit(S::AbstractStatistic, B::Int)`: 新しい `TwoSidedBootstrapLimit` オブジェクトを作成します。引数 `S` は `AbstractStatistic` オブジェクトです。引数 `B` はブートストラップの再現回数を示す整数です。
