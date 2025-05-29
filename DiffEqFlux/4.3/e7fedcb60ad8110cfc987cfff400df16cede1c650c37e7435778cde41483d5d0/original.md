```
u′, u = collocate_data(data, tpoints, kernel = TriangularKernel(), bandwidth=nothing)
u′, u = collocate_data(data, tpoints, tpoints_sample, interp, args...)
```

Computes a non-parametrically smoothed estimate of `u'` and `u` given the `data`, where each column is a snapshot of the timeseries at `tpoints[i]`.

For kernels, the following exist:

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

Additionally, we can use interpolation methods from [DataInterpolations.jl](https://github.com/SciML/DataInterpolations.jl) to generate data from intermediate timesteps. In this case, pass any of the methods like `QuadraticInterpolation` as `interp`, and the timestamps to sample from as `tpoints_sample`.
