```
    function BayesB(pi,v;estimatePi=false)
```

  * `pi` is the proportion of SNPs to be included in the model at each McMC cycel. If `estimatePi=true`, it is only used as a starting value.
  * `v` is the variance for the prior distribution of SNPs.
  * `estimatePi` is `true`if `pi` is estimated. By default it is ´false´
