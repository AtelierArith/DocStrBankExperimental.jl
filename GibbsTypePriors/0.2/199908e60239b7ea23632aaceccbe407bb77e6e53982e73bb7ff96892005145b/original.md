```
Pkn_NGG(n, β, σ)
```

Compute the prior probability mass to obtain k clusters over k=0 to k=n, either through direct computation or using the recursive computation for the Cnk, with arbitrary precision. Stable for large values of k. If this became unstable for small values of k, the function will print a warning and resort to using an approximation scheme based on the predictive distribution of Gibbs-type processes (Bystrova, 2020)

References:

  * Bystrova, D, Kon Kam King, G, Deslandes, F, Arbel, J. Approximating the clusters' prior distribution in Bayesian nonparametric models, 2020 (in preparation).

# Examples

```julia-repl
julia> GibbsTypePriors.Pkn_NGG(10, 100, 1.2, 0.6)
```
