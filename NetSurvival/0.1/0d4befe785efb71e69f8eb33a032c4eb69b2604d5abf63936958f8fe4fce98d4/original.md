```
GenPoharPerme
```

This method estimates net survival probabilities under the generalized pohar perme method, taking into account a copula for (E,P) as described in the reference paper. You may use it as: 

```
fit(GenPoharPerme(copula), @formula(Surv(time, status)~ x1 + x2), data, ratetable)
```

Note that `GenPoharPerme(::IndependenceCopula)` simply returns `PoharPerme`.

References: 

  * [Laverny2025](@cite) Laverny, O., Grafféo, N., & Giorgi, R. (2025). Non-parametric estimation of net survival under dependence between death causes. arXiv preprint arXiv:2502.09273.
