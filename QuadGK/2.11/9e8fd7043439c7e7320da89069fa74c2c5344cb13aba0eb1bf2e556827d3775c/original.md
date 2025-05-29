```
gauss(W, N, a, b; rtol=sqrt(eps), quad=quadgk)
```

Return a pair `(x, w)` of `N` quadrature points `x[i]` and weights `w[i]` to integrate functions on the interval `(a, b)` multiplied by the weight function `W(x)`.  That is, `sum(w .* f.(x))` approximates the integral `∫ W(x)f(x)dx` from `a` to `b`.

This function performs `2N` numerical integrals of polynomials against `W(x)` using the integration function `quad` (defaults to `quadgk`) with relative tolerance `rtol` (which defaults to half of the precision `eps` of the endpoints). This is followed by an O(N²) calculations. So, using a large order `N` is expensive.

If `W` has lots of singularities that make it hard to integrate numerically, you may need to decrease `rtol`.   You can also pass in a specialized quadrature routine via the `quad` keyword argument, which should accept arguments `quad(f,a,b,rtol=_,atol=_)` similar to `quadgk`.  (This is useful if your weight function has discontinuities, in which case you might want to break up the integration interval at the discontinuities.)

The precision of the calculations and return value is determined from the types of `a` and `b`.
