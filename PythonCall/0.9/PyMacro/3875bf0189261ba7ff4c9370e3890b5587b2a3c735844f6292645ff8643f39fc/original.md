```
@py expr
```

Evaluate the given expression using Pythonic semantics.

For example:

  * `f(x, y)` is translated to `pycall(f, x, y)`
  * `x + y` is translated to `pyadd(x, y)`
  * `x === y` is translated to `pyis(x, y)` (`x is y` in Python)
  * `x.foo` is translated to `pygetattr(x, "foo")`
  * `import x: f as g` is translated to `g = pyimport("x" => "f")` (`from x import f as g` in Python)

Compound statements such as `begin`, `if`, `while` and `for` are supported.

See the online documentation for more details.

!!! warning
    This macro is experimental. It may be modified or removed in a future release.

