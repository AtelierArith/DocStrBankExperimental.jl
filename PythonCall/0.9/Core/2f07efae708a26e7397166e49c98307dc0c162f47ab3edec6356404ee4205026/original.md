```
pyeval([T=Py], code, globals, locals=nothing)
```

Evaluate the given Python `code`, returning the result as a `T`.

If `globals` is a `Module`, then a persistent `dict` unique to that module is used.

By default the code runs in global scope (i.e. `locals===globals`). To use a temporary local scope, set `locals` to `()`, or to a `NamedTuple` of variables to include in the scope.

See also [`@pyeval`](@ref).

# Examples

The following computes `1.1+2.2` in the `Main` module as a `Float64`:

```
pyeval(Float64, "x+y", Main, (x=1.1, y=2.2))  # returns 3.3
```
