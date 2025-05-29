```
ubound([T, ] x::ArbOrRef)
```

Returns an upper bound of `x` as an `Arf`. If `T` is given convert to this type, supports `Arf` and `Arb`.

If `x` contains `NaN` it returns `NaN`.
