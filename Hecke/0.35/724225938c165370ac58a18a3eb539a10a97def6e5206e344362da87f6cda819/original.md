```
division_polynomial_univariate(E::EllipticCurve, n::Int, [x]) -> Poly
```

Compute the n-th univariate division polynomial of an elliptic curve defined over a field k following Mazur and Tate. By default the result is a univariate polynomial over the base ring of `E`. When `x` is given, the output is evaluated using the given value for `x`.

A triple of objects is returned:

  * The n-th division polynomial as a univariate polynomial with a mutiplicity  of 2 at the non-zero two-torsion points.
  * The n-th division polynomial as a univariate polynomial divided by the univariate 2-torsion polynomial when n is even.
  * The complementary factor, i.e. the first output divided by the second output.
