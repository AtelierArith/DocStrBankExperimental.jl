```
peff()
```

Computes the effective prior given cost function parameters. Arguments are either:

  * `ptar, cfa, cmiss`: Scalars or Vectors of the prior of a target, the cost of a false positive and the cost of a false negative
  * `dcf::DCF`: a `DCF` object containing `ptar`, `cfa` and `cmiss`.
