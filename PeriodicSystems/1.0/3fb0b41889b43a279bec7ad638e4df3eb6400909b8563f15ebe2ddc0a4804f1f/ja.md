```
pspole(psys::PeriodicStateSpace{PM}[,K]; kwargs...) -> val
```

周期システム `psys = (A(t),B(t),C(t),D(t))` に対して、周期行列 `A(t)` の特性指数（システム `psys` の*極*とも呼ばれる）を含む複素ベクトル `val` を返します。

基になる周期行列のタイプ `PM` に応じて、オプション引数 `K` とキーワード引数 `kwargs` は以下の値を持つことがあります：

  * `PM = PeriodicFunctionMatrix`、または `PM = PeriodicSymbolicMatrix`、または `PM = PeriodicTimeSeriesMatrix` の場合、`K` は `A(t)` のモノドロミー行列を表現するために使用される因子の数（デフォルト: `K = 1`）であり、`kwargs` は `PeriodicMatrices.pseig(::PeriodicFunctionMatrix)` のキーワード引数です；
  * `PM = HarmonicArray` の場合、`K` は `A(t)` のフーリエ級数を表現するために使用される調和成分の数（デフォルト: `K = max(10,nh-1)`、`nh` は `A(t)` の調和項の数）であり、`kwargs` は `PeriodicMatrices.psceig(::HarmonicArray)` のキーワード引数です；
  * `PM = FourierFunctionMatrix` の場合、`K` は `A(t)` のフーリエ級数を表現するために使用される調和成分の数（デフォルト: `K = max(10,nh-1)`、`nh` は `A(t)` の調和項の数）であり、`kwargs` は `PeriodicMatrices.psceig(::FourierFunctionMatrix)` のキーワード引数です；
  * `PM = PeriodicMatrix` または `PM = PeriodicArray` の場合、`K` は開始サンプル時間（デフォルト: `K = 1`）であり、`kwargs` は `PeriodicMatrices.psceig(::PeriodicMatrix)` のキーワード引数です；
