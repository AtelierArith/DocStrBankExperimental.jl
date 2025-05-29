```
DistributionComparison
```

This function calculate Vuong test and Clarke test for non nested distributions. This is necessary since it is possible to fit power law distribution to any data set. Function was implemented according to this [Non nested model selection for spatial count regression models with application to health insurance](https://mediatum.ub.tum.de/doc/1083601/1083601.pdf).

# Arguments

  * `d1`: First distribution to be compared.
  * `d2`: Second distribution to be compared.
  * `data`: Data to be compared.
  * `sig_level`: Significance level. Default is `0.05`.

# Returns

  * `DistributionComparison`: Struct containing all necessary information about comparison.
