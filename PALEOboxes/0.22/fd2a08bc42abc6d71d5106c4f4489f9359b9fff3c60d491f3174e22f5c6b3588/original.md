```
value_ad(x::ADT) -> x
```

Get scalar value from variable `x` (discarding any AD derivatives).

This can be used to exclude `x` from automatic differentation and hence a Jacobian calculation, eg where `x` is a small contribution but would make the Jacobian much denser.

Model code should implement this for any AD types used, eg

```
value_ad(x::SparsityTracing.ADval) = SparsityTracing.value(x)
value_ad(x::ForwardDiff.Dual) = ForwardDiff.value(x)
```
