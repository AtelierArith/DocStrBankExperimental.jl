```
spa{T<:Number}(lossDiff::Matrix{T}, method ; kwargs...)::SPATest
spa{T<:Number}(lossDiff::Matrix{T} ; kwargs...)
```

This function implements the SPA test proposed in Hansen (2005) "A Test for Superior Predictive Ability". 

Let x*0 denote a base-case forecast, x*k, k = 1, ..., K, denote K alternative forecasts, and y denote the forecast target. Let L(., .) denote a loss function. The first argument of spa is a matrix where the kth column of the matrix is created by the operation: 

L(x*k, y) - L(x*0, y) 

Note that the forecast loss comes first and the base case loss comes second. This is the opposite to what is described in Hansen's paper. 

The second method argument determines which methodology to use. Currently, only SPABoot is available and if this input type is provided, the keyword arguments are not needed. Alternatively, the user can omit the second argument, and then any keyword arguments will be passed to the SPABoot constructor. See ?SPABoot for more detail. The most relevant keyword arguments are:     alpha=0.05 <- The confidence level to use in the test 

```
kernelfunction=KernelEpanechnikov() <- The kernel function to use with HAC variance estimator. See ?hacvariance for more detail. 

bandwidth=-1 <- The bandwidth for HAC variance estimator. If bandwidth <= -1 then bandwidth is estimated using Politis (2003) "Adaptive Bandwidth Choice" 

blocklength=0.0 <- Block length to use with the bootstrap. Default of 0.0 implies
    the block length will be optimally estimated from the data use the method deemed
    most appropriate by the DependentBootstrap package (typically the selection procedure
    of Patton, Politis, and White (2009)). 

numresample=1000 <- Number of resamples to use when bootstrapping. 

bootmethod=:stationary <- Bootstrap methodology to use, where the default is the
    stationary bootstrap of Politis and Romano (1993)
```

The output of an SPA test is of type SPATest. Use ?SPATest for more information. 

Note, Hansen suggests using the Stationary Bootstrap implied HAC variance estimator, which is not currently supported in this package. However, note that any consistent HAC estimator is valid and in many cases may be preferred.
