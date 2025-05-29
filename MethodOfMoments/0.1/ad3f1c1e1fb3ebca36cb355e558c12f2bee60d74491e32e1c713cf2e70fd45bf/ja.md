```
fit(::Type{<:IteratedLinearGMM}, vce::CovarianceEstimator, data, eqs; kwargs...)
```

各イテレーションで重み行列が`vce`によって推定された分散共分散行列の逆として評価される線形反復GMM推定を行います。`data`は`Tables.jl`互換のデータテーブルです。`eqs`は変数の名前を指定します。このメソッドはパラメータが過剰同定されている場合に使用されます。詳細についてはドキュメントウェブサイトを参照してください。

# キーワード

  * `nocons::Bool=false`: 定数項を自動的に追加しない。
  * `winitial=:TSLS`: 初期重み行列; デフォルトで二段階最小二乗法のものを使用。
  * `θtol::Real=1e-8`: パラメータの収束を決定するための許容レベル。
  * `maxiter::Integer=10000`: 許可される最大イテレーション数。
  * `showtrace::Bool=false`: イテレーションが進むにつれて情報を印刷。
  * `initonly::Bool=false`: 推定を行わずに返されるオブジェクトを初期化。
  * `TF::Type=Float64`: 数値の型。
