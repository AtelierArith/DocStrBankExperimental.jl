```
posterior(sva::SparseVariationalApproximation{Centered})
```

Compute the approximate posterior [1] over the process `f = sva.fz.f`, given inducing inputs `z = sva.fz.x` and a variational distribution over inducing points `sva.q` (which represents $q(u)$ where `u = f(z)`). The approximate posterior at test points $x^*$ where $f^* = f(x^*)$ is then given by:

$$
q(f^*) = \int p(f | u) q(u) du
$$

which can be found in closed form.

[1] - Hensman, James, Alexander Matthews, and Zoubin Ghahramani. "Scalable variational Gaussian process classification." Artificial Intelligence and Statistics. PMLR, 2015.
