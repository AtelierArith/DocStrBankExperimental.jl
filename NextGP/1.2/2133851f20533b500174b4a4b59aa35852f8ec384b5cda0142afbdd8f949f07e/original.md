```
    function BayesRCπ(pi,class,v,annot;estimatePi=false)
```

  * `pi` is the vector of proportion of SNPs for each variance class. If `estimatePi=true`, it is only used as a starting value.
  * `class` is the vector of scales of common SPN variance for each variance class. The scales should be in the increasing order. For example, [0.0,0.0001,0.001,0.01].
  * `v` is the variance for the prior distribution of SNPs.
  * `annnot` is a matrix of annottations. Rows are SNPs, columnns are annnotation classes. Entries are binary coded, 0/1.
  * `estimatePi` is `true`if `pi` is estimated. By default it is ´false´
