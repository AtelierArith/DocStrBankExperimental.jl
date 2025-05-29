```
quotient_basis(polynomials; options...)
```

Returns a monomial basis of the quotient algebra of a zero-dimensional ideal.

If the input is not a Groebner basis, computes a Groebner basis. If the input is not a zero-dimensional ideal, an error is raised.

## Arguments

  * `polynomials`: an array of polynomials. Supports polynomials from   AbstractAlgebra.jl, Nemo.jl, and DynamicPolynomials.jl.

## Returns

  * `basis`: an array of monomials, a quotient basis.

## Possible Options

  * `ordering`: Specifies the monomial ordering. Available monomial orderings are:

      * `InputOrdering()` for inferring the ordering from the given `polynomials` (default),
      * `Lex()` for lexicographic,
      * `DegLex()` for degree lexicographic,
      * `DegRevLex()` for degree reverse lexicographic,
      * `WeightedOrdering(weights)` for weighted ordering,
      * `ProductOrdering(args...)` for block ordering,
      * `MatrixOrdering(matrix)` for matrix ordering.

    For details and examples see the corresponding documentation page.

## Example

Using AbstractAlgebra.jl:

```@example
using Groebner, Nemo
R, (x, y) = QQ["x", "y"]
quotient_basis([x*y^2 + x, y*x^2 + y])
```

## Notes

  * The function is thread-safe.
  * For AbstractAlgebra.jl and Nemo.jl, the function is most efficient for   polynomials over `GF(p)`, `Native.GF(p)`, and `QQ`.
