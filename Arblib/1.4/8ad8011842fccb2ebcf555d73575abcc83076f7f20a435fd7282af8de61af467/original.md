```
abs_lbound([T, ] x::Union{ArbOrRef,AcbOrRef})
```

Returns a lower bound of `abs(x)` as an `Arf`. If `T` is given convert to this type, supports `Arf` and `Arb`.

If `x` contains `NaN` it returns `NaN`.
