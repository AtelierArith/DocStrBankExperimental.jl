```
MCSBoot(data ; alpha, basecaseindex, kwargs...)
```

Method type for doing a MCS test using a dependent bootstrap. Relevant keyword arguments are: 

```
alpha=0.05 <- The confidence level to use in the test 

basecaseindex=1 <- The MCS does not have a natural basecase. However, the input data is a
	matrix of losses, not loss differentials, and the method itself considers every possible
	loss differential combination. This is far too many to check for determining
	the optimal block length for bootstrapping, so users who wish to auto-estimate
	the appropriate block length can specify a notional base case variable index
	for the purposes of computing a optimal block lengths of all loss differences
	relative to the base case.
blocklength=0.0 <- Block length to use with the bootstrap. Default of 0.0 implies
    the block length will be optimally estimated from the data use the method deemed
    most appropriate by the DependentBootstrap package (typically the selection procedure
    of Patton, Politis, and White (2009)). 

numresample=1000 <- Number of resamples to use when bootstrapping. 

bootmethod=:stationary <- Bootstrap methodology to use, where the default is the
    stationary bootstrap of Politis and Romano (1993)
```

Note, see the DependentBootstrap docs for more information on valid keyword arguments for the BootInput constructor.
