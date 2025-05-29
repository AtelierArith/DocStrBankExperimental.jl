```
posterior(la::LaplaceApproximation, lfx::LatentFiniteGP, ys)
```

Construct a Gaussian approximation `q(f)` to the posterior `p(f | y)` using the Laplace approximation. Solves for a mode of the posterior using Newton's method.
