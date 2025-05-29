```
 NUTS!(UDE, kwargs ...)
```

Performs Bayesian estimation on the parameters of a UDE using the No U-Turn Sampler (NUTS) algorithm.

# kwargs

  * `delta`: Step size used in NUTS adaptor. Default is `0.45`.
  * `samples`: Number of parameters sampled. Default is `500`.
  * `burnin`: Number of samples used as burn-in of Bayesian algorithm. Default is `samples/10`.
  * `verbose`: Should the training loss values be printed? Default is `true`.

```

```
