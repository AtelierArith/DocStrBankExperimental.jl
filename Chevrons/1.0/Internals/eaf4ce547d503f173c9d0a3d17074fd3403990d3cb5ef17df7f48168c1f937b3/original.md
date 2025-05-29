```
@chevrons ex
```

Recursively replace `>>` chained function calls.

  * `x >> f(y, z)` becomes `f(x, y, z)`
  * `x >> f(y, _, z)` becomes `f(y, x, z)`
  * `x >> f(y) >> g(z)` becomes `g(f(x, y), z)`

Also replaces `<<` in the other direction.

  * `f(y, z) << x` becomes `f(x, y, z)`
  * `f(y, __, z) << x` becomes `f(y, x, z)` (note the double underscore)
  * `x >> f(y) << z` becomes `f(z, x, y)`

Also `>>>` can be used to keep the previous value.

  * `x >>> f() >> g()` becomes `tmp = x; f(tmp); g(tmp)`
