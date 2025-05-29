```
unique_integer(x::ArbFieldElem)
```

Return a pair where the first value is a boolean and the second is an `ZZRingElem` integer. The boolean indicates whether the interval $x$ contains a unique integer. If this is the case, the second return value is set to this unique integer.
