```
lbound([T, ] x::ArbOrRef)
```

Returns a lower bound of `x` as an `Arf`. If `T` is given convert to this type, supports `Arf` and `Arb`.

If `x` contains `NaN` it returns `NaN`.
