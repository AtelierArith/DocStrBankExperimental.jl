```
RegularizatedSolution
```

最適解 x を格納するデータ型。λ は最適な λ で、solution は Optim 検索からの生の出力です。

```
x::AbstractVector
λ::AbstractFloat
solution::Optim.UnivariateOptimizationResults
```
