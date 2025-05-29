```
FixedPointDecimals.checked_rdiv(x::FD, y::FD) -> FD
```

Calculates `x / y`, checking for overflow errors where applicable.

The overflow protection may impose a perceptible performance penalty.

See also:

  * `Base.checked_div` for truncating division.
