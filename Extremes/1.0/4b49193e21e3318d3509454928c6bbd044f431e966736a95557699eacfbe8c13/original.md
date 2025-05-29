```
bic(fm:::MaximumLikelihoodAbstractExtremeValueModel)
```

Compute the Bayesian information criterion (BIC) of the fitted model by maximum likelihood method.

## Details

The BIC is defined as follows:

$BIC = k \log n - 2 \log \hat{L};$

where $k$ is the number of estimated parameters, $n$ is the number of data and $\hat{L}$ is the maximized value of the likelihood function for the model. 
