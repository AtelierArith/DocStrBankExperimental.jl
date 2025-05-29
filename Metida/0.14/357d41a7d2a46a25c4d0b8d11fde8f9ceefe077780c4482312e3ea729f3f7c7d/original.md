StatsBase.confint(br::BootstrapResult, n::Int; level::Float64=0.95, method=:bp, metric = :coef, delrml = false)

Confidence interval for bootstrap result.

*method:

  * :bp - bootstrap percentile;
  * :rbp - reverse bootstrap percentile;
  * :norm - Normal distribution;
  * :bcnorm - Bias corrected Normal distribution;
  * :jn - bias corrected (jackknife resampling).
