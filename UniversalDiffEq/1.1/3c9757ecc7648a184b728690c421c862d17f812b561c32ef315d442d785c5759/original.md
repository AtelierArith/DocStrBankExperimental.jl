```
 SGLD!(UDE, kwargs ...)
```

Performs Bayesian estimation on the parameters of an UDE using the Stochastic Gradient Langevin Dynamics (SGLD) sampling algorithm. At each step `t`, the stochastic update is provided by a random variable ε with mean 0 and noise η.

`math  ϵ = a*(b + t-1)^-γ`

# kwargs

  * `a`: Default is `10.0`.
  * `b`: Default is `1000`.
  * `γ`: Default is 0.9.
  * `samples`: Number of parameters sampled. Default is `500`.
  * `burnin`: Number of samples used as burn-in of Bayesian algorithm. Default is `samples/10`.
  * `verbose`: Should the training loss values be printed? Default is `true`.

```

```
