```
meanperformance(confusion::AbstractVector{ROCNums{Int64}}, metric::Function)
```

与えられたメトリックの平均パフォーマンスを混同行列のセットに対して取得します。

# 引数

  * `confusion::AbstractVector{ROCNums{Int64}}`: 混同行列
  * `̂metric::Function`: 評価に使用するパフォーマンスメトリック関数。
