```
exactpruning!(man::AbstractCutPruner, optimizer_constructor;
              ub=Inf, lb=-Inf, epsilon=1e-5)
```

支配されたカットをCutPruner `man` から削除します。

カットが支配されているかどうかを判断するためにLPソルバーを使用します。

# 引数

  * `man::AbstractCutPruner`   カットを削除するCut pruner
  * `optimizer_constructor`   LPを解決するために使用される最適化器
  * `ub::Union{Float64, Vector{Float64}}`   状態xの上限
  * `lb::Union{Float64, Vector{Float64}}`   状態xの下限
  * `epsilon::Float64`   プルーニングの許容誤差
