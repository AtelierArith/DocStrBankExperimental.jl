```
term(coef, mono::AbstractMonomialLike)
```

Returns a term with coefficient `coef` and monomial `mono`. There are two key difference between this and `coef * mono`:

  * `term(coef, mono)` does not copy `coef` and `mono` so modifying this term with MutableArithmetics may modifying the input of this function. To avoid this, call `term(MA.copy_if_mutable(coef), MA.copy_if_mutable(mono))` where `MA = MutableArithmetics`.
  * Suppose that `coef = (x + 1)` and `mono = x^2`, `coef * mono` gives the polynomial with integer coefficients `x^3 + x^2` which `term(x + 1, x^2)` gives a term with polynomial coefficient `x + 1`.

    term(p::AbstractPolynomialLike)

Converts the polynomial `p` to a term. When applied on a polynomial, it throws an `InexactError` if it has more than one term. When applied to a term, it is the identity and does not copy it. When applied to a monomial, it create a term of type `AbstractTerm{Int}`.
