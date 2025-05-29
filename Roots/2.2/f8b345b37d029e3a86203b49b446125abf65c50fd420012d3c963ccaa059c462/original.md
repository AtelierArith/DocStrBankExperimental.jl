```
Roots.AlefeldPotraShi()
```

Follows Algorithm 4.1 in "ON ENCLOSING SIMPLE ROOTS OF NONLINEAR EQUATIONS", by Alefeld, Potra, Shi; DOI: [10.1090/S0025-5718-1993-1192965-2](https://doi.org/10.1090/S0025-5718-1993-1192965-2).

The order of convergence is `2 + √5`; asymptotically there are 3 function evaluations per step. Asymptotic efficiency index is $(2+√5)^{1/3} ≈ 1.618...$. Less efficient, but can run faster than the related [`A42`](@ref) method.

Originally by John Travers.
