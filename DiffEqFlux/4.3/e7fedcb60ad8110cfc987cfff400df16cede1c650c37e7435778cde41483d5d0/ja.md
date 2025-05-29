```
u′, u = collocate_data(data, tpoints, kernel = TriangularKernel(), bandwidth=nothing)
u′, u = collocate_data(data, tpoints, tpoints_sample, interp, args...)
```

`data`を与えられたとき、各列が`tpoints[i]`での時系列のスナップショットである`u'`と`u`の非パラメトリックに平滑化された推定値を計算します。

カーネルには以下のものがあります：

  * EpanechnikovKernel
  * UniformKernel
  * TriangularKernel
  * QuarticKernel
  * TriweightKernel
  * TricubeKernel
  * GaussianKernel
  * CosineKernel
  * LogisticKernel
  * SigmoidKernel
  * SilvermanKernel

https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2631937/

さらに、[DataInterpolations.jl](https://github.com/SciML/DataInterpolations.jl)の補間手法を使用して、中間のタイムステップからデータを生成することができます。この場合、`interp`として`QuadraticInterpolation`のような任意の手法を渡し、サンプリングするタイムスタンプを`tpoints_sample`として渡します。
