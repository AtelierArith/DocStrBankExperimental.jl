```
approx_log_evidence(approx::<Approximation>, lfx::LatentFiniteGP, ys)
```

Compute an approximation to the log of the marginal likelihood (also known as "evidence") under the given `approx`imation to the posterior. The return value of `approx_log_evidence` can be used to optimise the hyperparameters of `lfx`.
