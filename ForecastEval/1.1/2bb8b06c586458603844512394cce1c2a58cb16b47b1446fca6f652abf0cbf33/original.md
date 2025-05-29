```
mcs(l::Matrix{<:Number}, method ; kwargs...)
mcs(l::Matrix{<:Number} ; kwargs...)
```

This function implements the MCS test proposed in Hansen, Lunde, Nason (2011) "The Model Confidence Set", Econometrica, 79 (2), pp. 453-497. 

Let x_k, k = 1, ..., K, denote K forecasts (from K different forecasting models), and y denote the forecast target. Let L(., .) denote a loss function. The first argument of mcs is a matrix where the kth column of the matrix is created by the operation: 

L(x_k, y) 

Note that unlike the Reality Check and SPA test, there is no base case for the MCS. 

The second method argument determines which methodology to use. Currently, only MCSBoot is available and if this input type is provided, the keyword arguments are not needed. Alternatively, the user can omit the second argument, and then any keyword arguments will be passed to the MCSBoot constructor. See ?MCSBoot for more detail. The most relevant keyword arguments are:     alpha=0.05 <- The confidence level to use in the test 

```
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

For more detail on the bootstrap options, please see the docs for the DependentBootstrap package. 

The output of a MCS test is of type MCSTest. Use ?MCSTest for more information. 

Note, if you are hitting RAM limits, type ?ForecastEval.MCSBootLowRAM at the REPL for more detail on an alternative algorithm that is also available. 

Note, for any developers, the main algorithm (associated with MCSBoot) still has the following potential performance issues: 

```
ISSUE 1: Some of the temporary arrays in the loops could probably be eliminated 

ISSUE 2: For MCS method A, I think the loop over K could be terminated as soon as cumulative p-values are greater than method.alpha. Need to double check this. 

ISSUE 3: Need to add option to do just max(abs) method or just sum(sq) method (or both)
```

Comments or pull requests on these issues would be most welcome on the package github page.
