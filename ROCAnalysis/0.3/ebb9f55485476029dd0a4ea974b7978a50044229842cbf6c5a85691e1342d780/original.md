```
DCF(ptar, cfa, cmiss)
```

Holds one or more cost functions with which the performance of a two-class classifier can be assessed.  Any of the fields can be either a scalar or an array. The cost function is  specified by:

  * `ptar`: The prior probability of a target class
  * `cfa`: The cost of a false alarm (false positive)
  * `cmiss`: The cost of a miss (false negative)
