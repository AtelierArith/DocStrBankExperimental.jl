```
conversion([::Type{T}, ]src::Dictionary, dest::Dictionary; options...)
```

Construct an operator that converts coefficients from the source dictionary to coefficients of the destination dictionary.

The conversion is exact, up to side-effects of finite-precision calculations.
