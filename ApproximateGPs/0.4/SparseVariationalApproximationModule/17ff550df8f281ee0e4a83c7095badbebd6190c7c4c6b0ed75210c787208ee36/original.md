```
posterior(sva::SparseVariationalApproximation{NonCentered})
```

Compute the approximate posterior [1] over the process `f = sva.fz.f`, given inducing inputs `z = sva.fz.x` and a variational distribution over inducing points `sva.q` (which represents $q(ε)$ where `ε = cholesky(cov(fz)).L \ (f(z) - mean(f(z)))`). The approximate posterior at test points $x^*$ where $f^* = f(x^*)$ is then given by:

$$
q(f^*) = \int p(f | ε) q(ε) du
$$

which can be found in closed form.

[1] - Hensman, James, Alexander Matthews, and Zoubin Ghahramani. "Scalable variational Gaussian process classification." Artificial Intelligence and Statistics. PMLR, 2015.
