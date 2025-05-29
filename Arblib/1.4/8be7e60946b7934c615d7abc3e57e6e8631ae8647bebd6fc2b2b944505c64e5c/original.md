```
getinterval([T, ] x::ArbOrRef)
```

Returns a tuple `(l, u)` representing an interval `[l, u]` enclosing the ball `x`, both of them are of type `Arf`. If `T` is given convert to this type, supports `Arf`, `BigFloat` and `Arb`.

If `x` contains `NaN` both `l` and `u` will be `NaN`.

See also [`getball`](@ref).
