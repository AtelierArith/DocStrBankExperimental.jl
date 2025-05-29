```
DMBoot(data ; alpha, bootinput_kwargs...)
```

Method type for doing a Diebold-Mariano test using a dependent bootstrap. A constructor that takes the data and several keyword arguments is provided. Relevant keyword arguments are: 

```
alpha=0.05 <- The confidence level to use in the test 

blocklength=0.0 <- Block length to use with the bootstrap. Default of 0.0 implies
    the block length will be optimally estimated from the data use the method deemed
    most appropriate by the DependentBootstrap package (typically the selection procedure
    of Patton, Politis, and White (2009)). 

numresample=1000 <- Number of resamples to use when bootstrapping. 

bootmethod=:stationary <- Bootstrap methodology to use, where the default is the
    stationary bootstrap of Politis and Romano (1993)
```

See the DependentBootstrap package docs for more info on bootstrap input keyword arguments.
