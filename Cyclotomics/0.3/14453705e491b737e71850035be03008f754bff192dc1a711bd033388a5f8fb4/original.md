```
Cyclotomic(coeffs::AbstractVector)
```

Element of `length(coeffs)`-th cyclotomic field with coefficients stored as `coeffs`.

To access the internals of a cyclotomic use API functions:

  * `conductor` - the conductor of a cyclotomic, i.e. the `n` used currently for storage. This might not be the minimal embeding field of a cyclotomic.
  * `coeffs` - returns a reference to the underlying vector containing the coefficients.
  * `getindex`/`setindex!` - use `α[i]` to access the coefficient at `i`-th power of the root of unity (in a circular fashion).
  * `values`/`exponents` - paired iterators over *non zero* coefficients/exponents corresponding to *non-zero* coefficients
  * `normalform!` - bring a cyclotomic to its unique representation as given by Zumbroich basis (also available in non-modifying form).

Iteration over non-zero coefficients in `Cyclotomic` is provided by `exps_coeffs` which produces pairs `(exp, coeff)` of exponent and corresponding coefficient.
