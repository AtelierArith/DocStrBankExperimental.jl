```
unitless(x)
```

yields `x` without its units if any. `x` may be a number or a numeric type. In the latter case, `unitless` behaves like `bare_type`.

Compared to `ustrip` from the `Unitful` package, argument can be a numeric type and, of course, `unitless` only requires the lightweight `TypeUtils` package to be loaded.
