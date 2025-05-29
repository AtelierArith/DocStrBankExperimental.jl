```
pywith(f, o, d=nothing)
```

Equivalent to `with o as x: f(x)` in Python, where `x` is a `Py`.

On success, the value of `f(x)` is returned.

If an exception occurs but is suppressed then `d` is returned.
