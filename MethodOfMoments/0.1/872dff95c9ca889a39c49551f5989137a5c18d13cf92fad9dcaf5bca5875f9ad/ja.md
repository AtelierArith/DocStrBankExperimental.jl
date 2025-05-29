```
fit(::Type{<:JustIdentifiedLinearGMM}, vce::CovarianceEstimator, data, eqs; kwargs...)
```

分散共分散行列が `vce` によって推定された状態で、過不足なく特定された線形GMM推定を行います。`data` は `Tables.jl` 互換のデータテーブルです。`eqs` は変数の名前を指定します。詳細についてはドキュメントウェブサイトを参照してください。

# キーワード

  * `nocons::Bool=false`: 定数項を自動的に追加しない。
  * `initonly::Bool=false`: 推定を行わずに返されるオブジェクトを初期化する。
  * `TF::Type=Float64`: 数値の型。
