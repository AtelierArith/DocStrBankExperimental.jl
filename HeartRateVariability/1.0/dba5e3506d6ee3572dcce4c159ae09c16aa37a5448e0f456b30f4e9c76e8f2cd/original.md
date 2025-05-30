```
nonlinear(n,m=2,r=6)
```

Arguments:

  * n: the array that contains the NN-inetrvals
  * m: the embedding dimension, default=2
  * r: the tolerance, default=6

Results:

  * apen: the approximate entropy
  * sampen: the sample entropy
  * hurst: the hurst exponent (only valid if the length of n is >= 100)
  * renyi0, renyi1, renyi2: the Rényi entropy of order 0,1 and 2
