```
normalform(basis, to_be_reduced; options...)
```

Computes the normal form of polynomials `to_be_reduced` with respect to a Groebner basis `basis`.

## Arguments

  * `basis`: an array of polynomials, a Groebner basis. Supports polynomials from   AbstractAlgebra.jl, Nemo.jl, and DynamicPolynomials.jl.
  * `to_be_reduced`: either a single polynomial or an array of polynomials.   Supports polynomials from AbstractAlgebra.jl, Nemo.jl, and   DynamicPolynomials.jl.

## Returns

  * `reduced`: either a single polynomial or an array of polynomials, the normal forms.

## Possible Options

  * `check`: Check if `basis` forms a Groebner basis. Default is `true`.
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

Fining the normal form a single polynomial:

```@example
using Groebner, DynamicPolynomials
@polyvar x y;
normalform([y^2 + x, x^2 + y], x^2 + y^2 + 1)
```

Or, reducing two polynomials at a time:

```@example
using Groebner, DynamicPolynomials
@polyvar x y;
normalform([y^2 + x, x^2 + y], [x^2 + y^2 + 1, x^10*y^10])
```

## Notes

  * The function is thread-safe.
  * For AbstractAlgebra.jl and Nemo.jl, the function is most efficient for   polynomials over `GF(p)`, `Native.GF(p)`, and `QQ`.
  * The default algorithm is probabilistic (with `certify=false`). Results are   correct with high probability, however, no precise bound on the probability   is known.
