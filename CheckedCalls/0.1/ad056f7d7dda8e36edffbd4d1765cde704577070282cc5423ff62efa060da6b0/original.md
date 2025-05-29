```
checkedcall(f, args...)
checkedcall(f)
```

Calls `f(args...)`, checks the result for abnormalities, and either returns the result or throws an exception.

`checkedcall(f)(args...)` is equivalent to `checkedcall(f, args...)`.

By default, checks the return value with `containsnan`.

`checkedcall` should be specialized if the underlying cause of the abnormality can be determined more precisely without undue computational overhead. For example for

```julia
chained(f, g, x) = f(g(x))
```

One may want to specialize

```julia
function checkedcall(::typeof(chained), f, g, x)
    checkedcall(f, checkedcall(g, x))
end
```

`checkedcall` may also be specialized to perform additional output (and input) value checks for specific functions, checks do not need to be limited to `NaN` values.
