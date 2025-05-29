kolmogorov*smirnov*test

Calculate [Kolmogorov Smirnov test](https://www.encyclopediaofmath.org/index.php/Kolmogorov-Smirnov_test) on given data and distribution.

# Arguments

  * `dat::AbstractArray`: Data to be tested.
  * `d::UnivariateDistribution`: Distribution to be tested (`ContinuousPowerLaw` or `DiscretePowerLaw`).
  * `xmin::Number`: Minimum value of data to be considered.
  * `xmax::Int64`: Maximum value of data to be considered. Default is `1e5`.

# Returns

  * `KS::Float64`: Kolmogorov-Smirnov distance between the data and the distribution. It is the maximum absolute difference between the empirical and theoretical cumulative distribution functions (`cdf
