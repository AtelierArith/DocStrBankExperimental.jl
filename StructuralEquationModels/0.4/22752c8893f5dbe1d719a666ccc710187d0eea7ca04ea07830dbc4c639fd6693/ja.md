```
SemObservedCovariance(;
    specification,
    obs_cov,
    nsamples,
    obs_mean = nothing,
    observed_vars = nothing,
    kwargs...)
```

観測データを提供せずに、観測変数の共分散（`obs_cov`）と平均（`obs_means`）を用いて[`SemObserved`](@ref)を構築します。

[`SemObservedCovariance`](@ref)オブジェクトを返します。

# 引数

  * `obs_cov`: 観測変数の事前計算された共分散行列
  * `nsamples::Integer`: `obs_cov`と`obs_means`を計算するために使用されるサンプル数（観測データポイント）
  * `obs_mean`: 観測変数の事前計算された平均（オプション）
  * `observed_vars::AbstractVector`: 観測変数のID（`obs_cov`行列の行と列）
  * `specification`: オプションのSEM仕様（[`SemSpecification`](@ref））
