```
leading_ideal(polynomials; options...)
```

Returns generators of the ideal of the leading terms.

If the input is not a Groebner basis, computes a Groebner basis.

## Arguments

  * `polynomials`: an array of polynomials. Supports polynomials from   AbstractAlgebra.jl, Nemo.jl, and DynamicPolynomials.jl.

## Returns

  * `basis`: the basis of the ideal of the leading terms.

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
leading_ideal([x*y^2 + x, y*x^2 + y])
```

## Notes

  * The function is thread-safe.
  * For AbstractAlgebra.jl and Nemo.jl, the function is most efficient for   polynomials over `GF(p)`, `Native.GF(p)`, and `QQ`.
