```
rc(lD::Matrix{T}, method ; kwargs)
rc(lD::Matrix{T} ; kwargs)
```

This function implements the test proposed in White (2000) "A Reality Check for Data Snooping" following the methodology in Hansen (2005). 

Let x*0 denote a base-case forecast, x*k, k = 1, ..., K, denote K alternative forecasts, and y denote the forecast target. Let L(., .) denote a loss function. The first argument of rc is a matrix where the kth column of the matrix is created by the operation: 

L(x*k, y) - L(x*0, y) 

Note that the forecast loss comes first and the base case loss comes second. This is the opposite to what is described in White's paper. 

The second method argument determines which methodology to use. Currently, only RCBoot is available and if this input type is provided, the keyword arguments are not needed. Alternatively, the user can omit the second argument, and then any keyword arguments will be passed to the RCBoot constructor. See ?RCBoot for more detail. The most relevant keyword arguments are:     alpha=0.05 <- The confidence level to use in the test 

```
blocklength=0.0 <- Block length to use with the bootstrap. Default of 0.0 implies
    the block length will be optimally estimated from the data use the method deemed
    most appropriate by the DependentBootstrap package (typically the selection procedure
    of Patton, Politis, and White (2009)). 

numresample=1000 <- Number of resamples to use when bootstrapping. 

bootmethod=:stationary <- Bootstrap methodology to use, where the default is the
    stationary bootstrap of Politis and Romano (1993)
```

The output of a Reality Check test is of type RCTest. Use ?RCTest for more information.
