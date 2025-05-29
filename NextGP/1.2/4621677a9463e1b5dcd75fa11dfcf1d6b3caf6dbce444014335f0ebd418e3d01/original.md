```
    function BayesPR(r,v)
```

  * `r` is the region size. In other words, the number of SNPs that share a common variance.

      * `1`: each SNP has its own (co)variance
      * `99`: SNPs on the same chromosome has the same (co)variance
      * `9999`: All SNPs have the same (co)variance
      * One can define any other region size, for example, 30, 40 or 100
  * `v` is an estimate of the variance for the distribution of SNPs
