```
PolyZonoForward{A<:PolynomialApproximation,N,R} <: ForwardAlgorithm
```

Forward algorithm based on poynomial zonotopes via polynomial approximation from [Kochdumper0AB23](@citet).

### Fields

  * `polynomial_approximation` – method for polynomial approximation
  * `reduced_order`          – order to which the result will be reduced after                               each layer
  * `compact`                  – predicate for compacting the result after each                               layer

### Notes

The default constructor takes keyword arguments with the following defaults:

  * `polynomial_approximation`: `RegressionQuadratic(10)`, i.e., quadratic regression with 10 samples
  * `compact`: `() -> true`, i.e., compact after each layer

See the subtypes of `PolynomialApproximation` for available polynomial approximation methods.
