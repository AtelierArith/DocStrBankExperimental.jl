```
GraphPolynomial{METHOD} <: AbstractProperty
GraphPolynomial(; method=:finitefield, kwargs...)
```

Compute the graph polynomial, e.g. for [`IndependentSet`](@ref) problem, it is the independence polynomial. The `METHOD` type parameter can be one of the following symbols

## Method Argument

  * `:finitefield`, uses finite field algebra to fit the polynomial.

      * The corresponding tensor element type is [`Mods.Mod`](@ref),
      * It does not have round-off error,
      * GPU is supported,
      * It accepts keyword arguments `maxorder` (optional, e.g. the MIS size in the [`IndependentSet`](@ref) problem).
  * `:polynomial` and `:laurent`, use (Laurent) polynomial numbers to solve the polynomial directly.

      * The corresponding tensor element types are [`Polynomial`](https://juliamath.github.io/Polynomials.jl/stable/polynomials/polynomial/#Polynomial-2) and [`LaurentPolynomial`](https://juliamath.github.io/Polynomials.jl/stable/polynomials/polynomial/#Polynomials.LaurentPolynomial).
      * It might have small round-off error depending on the data type for storing the counting.
      * It has memory overhead that linear to the graph size.
  * `:fft`, use fast fourier transformation to fit the polynomial.

      * The corresponding tensor element type is `Base.Complex`.
      * It has (controllable) round-off error.
      * BLAS and GPU are supported.
      * It accepts keyword arguments `maxorder` (optional) and `r`,   if `r > 1`, one has better precision for coefficients of large order, if `r < 1`,   one has better precision for coefficients of small order.
  * `:fitting`, fit the polynomial directly.

      * The corresponding tensor element type is floating point numbers like `Base.Float64`.
      * It has round-off error.
      * BLAS and GPU are supported, it is the fastest among all methods.

Graph polynomials are not defined for weighted constraint satisfaction problems.
