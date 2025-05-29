```
dic(chain::Chains, logpdf::Function) -> (DIC, pD)
```

Compute the deviance information criterion (DIC). (Smaller is better)

Note: DIC assumes that the posterior distribution is approx. multivariate Gaussian and tends to select overfitted models.

## Returns:

  * `DIC`: The calculated deviance information criterion
  * `pD`: The effective number of parameters

## Usage:

```
chn ... # sampling results
lpfun = function f(chain::Chains) # function to compute the logpdf values
    niter, nparams, nchains = size(chain)
    lp = zeros(niter + nchains) # resulting logpdf values
    for i = 1:nparams
        lp += map(p -> logpdf( ... , x), Array(chain[:,i,:]))
    end
    return lp
end

DIC, pD = dic(chn, lpfun)
```
