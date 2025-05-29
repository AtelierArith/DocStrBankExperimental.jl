```
@inplace a = f(args...)
@inplace a += expr
```

Compute `f(args...)` resp. `+(a, expr)` and assign the result to `a`. If `a` is mutable, possibly modify its value in-place.

In the case where `a` is mutable, it is an implementation detail whether its value is actually modified. For this reason, one should use this operation only on values for which the current stackframe holds the only reference; e.g. by using `deepcopy`.
