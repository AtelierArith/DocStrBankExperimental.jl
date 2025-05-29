```
PNTerm{T,PNOrder,c⁻¹Exponent}
```

This object represents a single term in a PNExpansion.  It has a single field: `coeff`, which is the coefficient of the term.  The type parameter `T` is the type of the coefficient.  The type parameter `PNOrder` is a half-integer (just as in [`PNSystem`](@ref)s) representing the PN order of the expansion.  And the type parameter `c⁻¹Exponent` is an integer representing the exponent of the PN expansion parameter $1/c$.

`PNTerm`s can be multiplied and divided by scalars and exponentiated by integers, to produce another `PNTerm`.  They can also be added to other `PNTerm`s to produce a `PNExpansion`.

A simple way to define a `PNTerm` or a `PNExpansion` is to define the PN expansion parameter

```julia
c = PNExpansionParameter(pnsystem)
```

and use that naturally in formulas, as in

```julia
e = 1 + (v/c)^2 * (-ν/12 - 3//4) + (v/c)^4 * (-ν^2/24 + 19ν/8 - 27//8)
```

Any exponent higher than the desired `PNOrder` will be automatically set to zero.

Useful facts:

  * `v` has order `1/c`
  * `x` has order `1/c^2`
  * `γ` has order `1/c^2`
  * `1/r` has order `1/c^2`
