```
ArbFloat(x)
ArbFloat(x; [bits])
ArbFloat(x; [digits [, base=10]])
```

  * ArbFloat(x) == ArbFloat(x, bits=workingprecision(ArbFloat))
  * ArbFloat(x, digits=digits, base=2) == ArbFloat(x, bits=digits)
  * ArbFloat(x, digits=digits, base=10) == ArbFloat(x, digits=digits)

ArbFloats are arbitrary precision binary floating-point numbers with some specific precision established at construction.

The precision of an ArbFloat must be >= 24 bits or >= 8 digits.

Negative zero, unsigned Infinity, NaNs with distinct payloads are not supported.

See also: [`ArbReal`](@ref), [`ArbComplex`](@ref), [`workingprecision`](@ref), [`displayprecision`](@ref)
