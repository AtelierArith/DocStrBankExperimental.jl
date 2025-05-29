```
eval_performance(
  solver::RBSolver,
  feop::ParamOperator,
  fesnaps::AbstractSnapshots,
  rbsnaps::AbstractSnapshots,
  festats::CostTracker,
  rbstats::CostTracker
  ) -> ROMPerformance
```

引数:

  * `solver`: 簡約化された問題のソルバー
  * `feop`: PDEを表すFEオペレーター
  * `fesnaps`: FE解のオンラインスナップショット
  * `rbsnaps`: `fesnaps`の簡約化近似
  * `festats`: `fesnaps`を計算するために必要な時間とメモリ消費
  * `rbstats`: `rbsnaps`を計算するために必要な時間とメモリ消費

返り値は、`rbsnaps`と`fesnaps`の間の（相対的な）誤差、および`rbstats`と`festats`の間の計算速度向上を示す、簡約化アルゴリズムの性能です。
