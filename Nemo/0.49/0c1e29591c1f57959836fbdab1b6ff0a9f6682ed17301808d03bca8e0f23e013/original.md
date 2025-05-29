```
rand(r::ArbField; randtype::Symbol=:urandom)
```

Return a random element in given Arb field.

The `randtype` default is `:urandom` which return an `ArbFieldElem` contained in $[0,1]$.

The rest of the methods return non-uniformly distributed values in order to exercise corner cases. The option `:randtest` will return a finite number, and `:randtest_exact` the same but with a zero radius. The option `:randtest_precise` return an `ArbFieldElem` with a radius around $2^{-\mathrm{prec}}$ the magnitude of the midpoint, while `:randtest_wide` return a radius that might be big relative to its midpoint. The `:randtest_special`-option might return a midpoint and radius whose values are `NaN` or `inf`.
