```
DMHAC(data ; alpha::Float64=0.05, kernelfunction, bandwidth::Int=-1)
```

Method type for doing a Diebold-Mariano test using a HAC variance estimator. A constructor that takes the data and three keyword arguments is provided. Relevant keyword arguments are: 

```
alpha <- The confidence level for the test 

kernelfunction <- Kernel function to use in HAC variance estimator. Valid values are
    KernelEpanechnikov(), KernelGaussian(), KernelUniform(), KernelBartlett(). You can
    also :epanechnikov, :gaussian, :uniform, :bartlett, or String variants of these symbols. 

bandwidth <- Bandwidth to use in HAC variance estimator (set less than or equal to -1 to estimate bandwidth using Politis (2003) "Adaptive Bandwidth Choice")
```
