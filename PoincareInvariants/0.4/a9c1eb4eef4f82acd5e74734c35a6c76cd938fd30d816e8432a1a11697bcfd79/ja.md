```
FirstPoincareInvariant{T, D}(θ::θT, N::Integer, plan::P)
```

は、数値型 `T`、位相空間次元 `D`、微分形式 `θ`、点の数 `N` および `plan` を指定して、積分不変量を計算するための `FirstPoincareInvariant` セットアップオブジェクトを構築します。点の数は正確に `N` であるとは限らないことに注意してください。実際に使用される数は実装に依存し、`N` より小さくなることはなく、あまり大きくもなりません。
