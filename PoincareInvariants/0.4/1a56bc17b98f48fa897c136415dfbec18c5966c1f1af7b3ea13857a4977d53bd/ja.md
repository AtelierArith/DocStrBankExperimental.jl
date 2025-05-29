```
SecondPoincareInvariant{T, D}(ω, N, P::Type=DEFAULT_SECOND_PLAN)
```

は、数値型 `T`、位相空間次元 `D`、微分形式 `ω`、点指定 `N` および `plan` 型 `P` を与えられたときに、積分不変量を計算するための `SecondPoincareInvariant` セットアップオブジェクトを構築します。これは初期化され、将来の計算に使用されます。

プラン型はデフォルトで `DEFAULT_SECOND_PLAN` に設定されており、現在は `SecondChebyshevPlan` に設定されています。ポイントの数は正確に `N` であるとは限らないことに注意してください。実際に使用される数は実装に依存し、`N` よりも小さくはなく、あまり大きくもないことが保証されています。`SecondFinDiffPlan` の場合、非正方形グリッドを求める場合は、ポイントのグリッドをタプル `(Nx, Ny)` として指定することもできます。
