```
RCBoot(data ; alpha::Float64=0.05, bootinput_kwargs...)
```

Method type for doing a Reality Check using a dependent bootstrap. A constructor that takes the data and several keyword arguments is provided. The data refers to the loss differences for each forecast relative to the basecase. Use ?rc for more detail. Relevant keyword arguments are:     alpha=0.05 <- The confidence level to use in the test 

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

See the DependentBootstrap package docs for more info on bootstrap input keyword arguments.
