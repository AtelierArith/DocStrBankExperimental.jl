```
@pyconst ex
```

Equivalent to `Py(ex)` but always returns the exact same Julia object.

That is, if `foo() = @pyconst ex` then `foo() === foo()`.

The expression `ex` is evaluated the first time the code is run.

If `ex` is a string literal, the string is interned.

Do not use this macro at the top level of a module. Instead, use `pynew()` and `pycopy!()`.
