```
LaplaceEM(model, Estep_optimizer = Optimizer(), derivative_threshold = 1e-3, iterations = 10, stopper = () -> false)
```

Implements the Expectation-Maximization (EM) method with Laplace approximation, as described e.g. in [Huys et al. (2012)](http://dx.doi.org/10.1371/journal.pcbi.1002410).
