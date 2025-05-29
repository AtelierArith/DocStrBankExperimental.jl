```
loglikelihood(lik::SimulatorLikelihood, args...)
```

Evaluates the log-lielihood of `lik` on the current observable state by constructing the `predictive_distribution` and evaluating the `logpdf` of the data.
