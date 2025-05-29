```
Pkn_NGG(k, n, β, σ)
```

Compute the prior probability mass to obtain k clusters, either through direct computation or using the recursive computation for the Cnk, with arbitrary precision. Stable for large values of k, the function may become unstable for small values of k. If this were the case, the function would print a warning and resort to using an approximation scheme based on the predictive distribution of Gibbs-type processes (Bystrova, 2020)

References:

  * Bystrova, D, Kon Kam King, G, Deslandes, F, Arbel, J. Approximating the clusters' prior distribution in Bayesian nonparametric models, 2020 (in preparation).

# Examples

```julia-repl
julia> GibbsTypePriors.Pkn_NGG(10, 100, 1.2, 0.6)
```
