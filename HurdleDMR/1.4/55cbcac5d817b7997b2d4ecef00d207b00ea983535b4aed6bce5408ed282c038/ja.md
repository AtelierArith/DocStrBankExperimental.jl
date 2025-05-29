```
predict(m,newcovars; <キーワード引数>)
```

フィットしたDMRPathsオブジェクトと与えられたnewcovarsを使用してカウントを予測します。

# 例:

```julia
  m = fit(DMRPaths,covars,counts)
  newcovars = covars[1:10,:]
  countshat = predict(m, newcovars; select=MinAICc())
```

# 引数

  * `m::DMRPaths` フィットしたDMRPathsモデル（DMRCoefsは現在サポートされていません）
  * `newcovars` mをフィットするために使用されたのと同じ次元のn-by-pの共変量行列。

# キーワード

  * `select=MinAICc()` [`coef(::RegularizationPath)`](@ref)を参照してください。
  * `kwargs...` 各カテゴリj=1..size(counts,2)のpredict()に渡される追加のキーワード引数。
