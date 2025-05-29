```
maf_weights(x::SnpArray; max_weight::T = Inf)
```

Calculates the prior weight based on minor allele frequencies. 

Returns an array of weights where `w[i] = 1 / (2 * sqrt(p[i] (1 - p[i]))) ∈ (1, ∞).` Here `p` is the minor allele frequency computed by `maf()` in SnpArrays. 

  * `x`: A SnpArray
  * `max_weight`: Maximum weight for any predictor. Defaults to `Inf`.
