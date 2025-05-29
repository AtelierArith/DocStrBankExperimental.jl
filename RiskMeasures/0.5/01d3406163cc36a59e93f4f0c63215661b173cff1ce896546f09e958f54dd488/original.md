```
EVaR(x̃, α; βmin = 1e-5, βmax = 100, reciprocal = false, distribution = false)
```

Compute the EVaR risk measure of the random variable `x̃` with risk level `α` in [0,1].

```
EVaR(values, pmf, α; ...)
```

Compute EVaR for a discrete random variable with `values` and the probability mass function `pmf`.

When `α = 1`, the function computes the expected value, and when `α = 0`, then the  function computes the essential infimum (a minimum value with positive probability).

The function solves

$$
\max_{β ∈ [βmin, βmax]} \operatorname{ERM}_β (x̃) - β^{-1} \log (1/(α)).
$$

Large values of `βmax` may cause the computation to overflow.

If `reciprocal = false`, then the quasi-concave problem above is solved directly. If `reciprocal = true`, then the optimization is reformulated in terms of `λ = 1/β` to get a concave function that can be solved (probably) more efficiently

The function implicitly assumes that all elements of the probability space have non-zero probability. 

Returns the EVaR and the value β that attains the maximum above.

See: Ahmadi-Javid, A. “Entropic Value-at-Risk: A New Coherent Risk Measure.” Journal of Optimization Theory and Applications 155(3), 2012.
