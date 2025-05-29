```
FirstPoincareInvariant{T, D}(θ::θT, N::Integer, P::Type=DEFAULT_FIRST_PLAN)
```

は、数値型 `T`、位相空間次元 `D`、微分形式 `θ`、点の数 `N`、および初期化され、将来の計算に使用される `plan` 型 `P` を指定して、積分不変量を計算するための `FirstPoincareInvariant` セットアップオブジェクトを構築します。

プラン型はデフォルトで `DEFAULT_FIRST_PLAN` に設定されており、現在は `FirstFourierPlan` に設定されています。
