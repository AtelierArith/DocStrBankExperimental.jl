maxperformance(confusion::AbstractVector{ROCNums{Real}}, metric::Function)

与えられたメトリックの最大パフォーマンスを混同行列のセットに対して取得します。

# 引数

  * `confusion::AbstractVector{ROCNums{Real}}`: 混同行列。
  * `̂metric::Function`: 評価に使用するパフォーマンスメトリック関数。
