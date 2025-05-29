```
(graph,cref)=graph_bbc_exp(k;T=Float64)
```

Computes a polynomial evaluation approximating the exponential using `k` matrix multiplications following the procedure in the reference. The coefficients are directly copied from the paper.

The evaluation is embedded in the `degopt`-format, see [`graph_degopt`](@ref), and for `k< 3`, the evaluation is using the Paterson–Stockmeyer method.

**Reference**

1. P. Bader, S. Blanes, and F. Casas. "Computing the matrix exponential with an optimized Taylor polynomial approximation". Mathematics, 7(12), 2019. DOI: [10.3390/math7121174](https://doi.org/10.3390/math7121174)
