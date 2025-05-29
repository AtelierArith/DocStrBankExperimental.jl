```
e_bwd=compute_bnd_rel_bwd_err(
    f,
    graph::Compgraph{T};
    coefftype = T,
    numterms = 100,
    numdigits = 100,
)
```

Compute a bound on the relative backward error of the function `f`.

The returned function $e_{bwd}$ is a bound on the relative backward error of the polynomial underlying the computational graph `graph`, seen as an approximant to `f`. For the underlying polynomial $p$, the function returns a bound on `|δ|` where `δ` is such that $f(z+δ) = p(z)$.

The first argument `f` is a symbol. Currently supported values include:

  * `:exp` The bound is computed by means of the identity δ = log((exp(-z) p(z)-1)+1). The code computes the series expansion of the right-hand side of the equation, truncates it to the first `numterms` coefficients, bounds each coefficient of the ensuing polynomial with its absolute value. The computation uses `numdigits` digits of precision.
