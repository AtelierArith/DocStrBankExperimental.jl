```
ArbComplex(x)
ArbComplex(x; [bits])
ArbComplex(x; [digits [, base=10]])

ArbComplex(re, im)
ArbComplex(re, im; [bits])
ArbComplex(re, im; [digits [, base=10]])
```

  * `ArbComplex`(re, im) == `ArbComplex`(re, im, bits=workingprecision(ArbComplex))
  * `ArbComplex`(re, im, digits=digits, base=2) == `ArbComplex`(re, im, bits=digits)
  * `ArbComplex`(re, im, digits=digits, base=10) == `ArbComplex`(re, im, digits=digits)

`ArbComplexs` are arbitrary precision complex binary floating-point regions with some specific precision established at construction.

The precision of an `ArbComplex` must be >= 24 bits or >= 8 digits.

Internally, an `ArbComplex` represents as a pair of `ArbReal`, where the real part and the imaginary part are each intervals given by midpoint and radius (half-width of the interval). This representation serves as a *ball* over the complex numbers. Calculations with `ArbComplex` generate results that are assured to contain the true mathematical result. There is no a priori assurance on the width of the interval that results. Good practice is to set the precision substantively greater than the precision of the resultant width required, and to check the radius of results.

See also: [`ArbFloat`](@ref), [`ArbReal`](@ref), [`ball`](@ref), [`setball`](@ref), [`midpoint`](@ref), [`radius`](@ref)
