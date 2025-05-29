```
fit(::Type{<:IteratedGMM}, solvertype, vce::CovarianceEstimator,
    g, dg, params, nmoment::Integer, nobs::Integer; kwargs...)
```

非線形反復GMM推定を`solvertype`のソルバーで実施し、各反復での重み行列は`vce`によって推定された分散共分散行列の逆として評価されます。モーメント条件とその導関数は`g`と`dg`として指定されます。パラメータの名前、モーメント条件の数、および観測の数はそれぞれ`params`、`nmoment`、`nobs`として提供されます。詳細についてはドキュメントウェブサイトを参照してください。

# キーワード

  * `preg=nothing`: モーメント条件を評価する前にデータフレームを処理するための関数。
  * `predg=nothing`: モーメント条件の導関数を評価する前にデータフレームを処理するための関数。
  * `winitial=I`: 初期重み行列; デフォルトでは単位行列を使用。
  * `θtol::Real=1e-8`: パラメータの収束を決定するための許容レベル。
  * `maxiter::Integer=10000`: 許可される最大反復回数。
  * `ntasks::Integer=_default_ntasks(nobs*nmoment)`: 観測にわたってモーメント条件とその導関数を評価するために使用されるスレッドの数。
  * `showtrace::Bool=false`: 反復が進むにつれて情報を印刷します。
  * `initonly::Bool=false`: 推定を行わずに返されるオブジェクトを初期化します。
  * `solverkwargs=NamedTuple()`: 最適化ソルバーに渡されるキーワード引数としての`NamedTuple`。
  * `TF::Type=Float64`: 数値値の型。
