```
meanstdperformance(confusion::AbstractVector{ROCNums{Real}}, metric::Function)
```

与えられたメトリックの平均と標準偏差のパフォーマンスを、混同行列のセットに対して取得します。

# 引数

  * `confusion::AbstractVector{ROCNums{Real}}`: MLBaseからの混同行列オブジェクト
  * `̂metric::Function`: 評価に使用するパフォーマンスメトリック関数。
