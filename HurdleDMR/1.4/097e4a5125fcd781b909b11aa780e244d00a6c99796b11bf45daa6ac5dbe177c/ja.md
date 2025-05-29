```
predict(m,newcovars; <キーワード引数>)
```

フィットした HDMRPaths オブジェクトと与えられた newcovars を使用してカウントを予測します。

# 例:

```julia
  m = fit(HDMRPaths,covars,counts)
  newcovars = covars[1:10,:]
  countshat = predict(m, newcovars; select=MinAICc())
```

# 引数

  * `m::HDMRPaths` フィットした DMRPaths モデル (HDMRCoefs は現在サポートされていません)
  * `newcovars` m をフィットするために使用されたのと同じ次元の n-by-p 行列の共変量。

# キーワード

  * `select=MinAICc()` [`coef(::RegularizationPath)`](@ref) を参照してください。
  * `kwargs...` 各カテゴリ j=1..size(counts,2) に対して predict() に渡される追加のキーワード引数。
