```
likelihoodDistribution
```

A utility that uses multiple dispatch to take in one set of parameters for CausalGPSLC and the observed data, plus an intervention `doT`, and outputs the necessary matrices to compute MeanITE and CovITE, as well as other predictions, like directly predicting $Y_cf$.
