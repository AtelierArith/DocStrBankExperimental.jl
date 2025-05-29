```
HARVCE{LR<:LongRunVariance} <: CovarianceEstimator
```

Heteroskedasticity-autocorrelation-robust variance-covariance estimator with a long-run variance estimator of type `LR`.

# Fields

  * `lr::LR`: the long-run variance estimator.
  * `bw::Function`: bandwidth as a function of the number of periods in sample.
  * `cv::Function`: critical value as a function of the level of the test and the bandwidth.
  * `pv::Function`: p-value as a function of the test statistic and the bandwidth.
