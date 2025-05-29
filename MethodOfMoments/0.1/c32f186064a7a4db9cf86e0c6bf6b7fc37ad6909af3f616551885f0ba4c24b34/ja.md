```
BayesianGMM(vce::CovarianceEstimator,
    g, dg, params, nmoment::Integer, nobs::Integer; kwargs...)
```

ベイズ的準似然評価をサポートするオブジェクトを構築します。提供される引数は、非線形反復GMM推定と同じ方法で定義されています。詳細については、ドキュメントウェブサイトを参照してください。

# キーワード

  * `preg=nothing`: モーメント条件を評価する前にデータフレームを処理するための関数。
  * `predg=nothing`: モーメント条件の導関数を評価する前にデータフレームを処理するための関数。
  * `deriv=nothing`: 準事後関数の勾配がどのように計算されるかを指定します。
  * `ntasks::Integer=_default_ntasks(nobs*nmoment)`: 観測にわたってモーメント条件とその導関数を評価するために使用するスレッドの数。
  * `TF::Type=Float64`: 数値値の型。
