```
Infinite <: Real
```

A type with two values, `∞` and `-∞` (or `PosInf` and `NegInf`).

Arithmetic with values of other types will be promoted to either the other type if it supports infinity natively or to [`InfExtended`](@ref).
