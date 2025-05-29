```
kronrod(W, N, a, b; rtol=sqrt(eps), quad=quadgk)
```

Return a tuple `(x, w, wg)` of `N` quadrature points `x[i]` and weights `w[i]` to integrate functions on the interval `(a, b)` multiplied by the weight function `W(x)`, along with the weights `wg` of an embedded Gauss rule corresponding to `x[2:2:end]`, similar to the `gauss(W, N, a, b)` function and analogous to `kronrod(N)` (which only returns the `x ≤ 0` points for a constant weight function).

That is, `I = sum(w .* f.(x))` approximates the integral `∫ W(x)f(x)dx` from `a` to `b`.  And an error estimate is `abs(I - Ig)`, where `Ig` is the result `Ig = sum(wg .* f.(x[2:2:end]))` of the embedded Gauss rule.

This function performs `≈ 3N+3` numerical integrals of polynomials against `W(x)` using the integration function `quad` (defaults to `quadgk`) with relative tolerance `rtol` (which defaults to half of the precision `eps` of the endpoints). This is followed by an O(N²) calculations. So, using a large order `N` is expensive.
