```
pyjltype(x)
```

The subtype of `juliacall.AnyValue` which the Julia object `x` is wrapped as by `pyjl(x)`.

Overload `pyjltype(::T)` to define a custom conversion for your type `T`.
