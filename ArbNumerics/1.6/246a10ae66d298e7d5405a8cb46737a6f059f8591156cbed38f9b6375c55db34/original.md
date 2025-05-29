```
ArbReal(x)
ArbReal(x; [bits])
ArbReal(x; [digits [, base=10]])
```

  * `ArbReal`(x) == `ArbReal`(x, bits=workingprecision(ArbReal))
  * `ArbReal`(x, digits=digits, base=2) == `ArbReal`(x, bits=digits)
  * `ArbReal`(x, digits=digits, base=10) == `ArbReal`(x, digits=digits)

ArbReals are arbitrary precision binary floating-point regions with some specific precision established at construction.

The precision of an `ArbReal` must be >= 24 bits or >= 8 digits.

Internally, an `ArbReal` represents an interval given by its midpoint and radius (half-width of the interval). This representation serves as a *ball* over the real numbers.  Calculations with `ArbReals` generate results that are assured to contain the true mathematical result.  There is no a priori assurance on the width of the interval that results.  Good practice is to set the precision substantively greater than the precision of the resultant width required, and to check the radius of results.

See also: [`ArbFloat`](@ref), [`ArbComplex`](@ref), [`ball`](@ref), [`setball`](@ref), [`midpoint`](@ref), [`radius`](@ref)
