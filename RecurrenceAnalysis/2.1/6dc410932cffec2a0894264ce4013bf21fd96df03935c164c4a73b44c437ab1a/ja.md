```
distancematrix(x [, y = x], metric = "euclidean")
```

`x` と `y` の各点のペア間の距離を `metric` を使用して計算した行列を作成します。

時系列 `x` と `y` は `AbstractStateSpaceSet` であるか、データポイントが行にあるベクトルまたは行列である必要があります。データポイントの次元（または列の数）は `x` と `y` で同じでなければなりません。返される値は `n×m` 行列で、`n` は `x` の長さ（または行の数）、`m` は `y` の長さです。

メトリックは [`Distances` パッケージ](https://github.com/JuliaStats/Distances.jl) で定義された任意の `Metric` であり、デフォルトは `Euclidean()` です。
