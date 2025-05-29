```
(graph,cref)=graph_sid_exp(k;T=Float64)
```

Computes a polynomial evaluation approximating the exponential using `k` matrix multiplications following the procedure in the reference. The coefficients are directly copied from the paper.

The evaluation is embedded in the degopt-format, see [`graph_degopt`](@ref), using the function [`graph_sastre_yks_degopt`](@ref). Moreover, for `k<=3` it uses the Paterson–Stockmeyer method.

**Reference**

1. J. Sastre, J. Ibáñez, E. Defez. "Boosting the computation of the matrix exponential". Applied Mathematics of Computation, 340:206-220, 2019. DOI: [10.1016/j.amc.2018.08.017](https://doi.org/10.1016/j.amc.2018.08.017)
