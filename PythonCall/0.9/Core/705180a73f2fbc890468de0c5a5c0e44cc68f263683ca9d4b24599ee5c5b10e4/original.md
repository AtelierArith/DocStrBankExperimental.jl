```
pyexec([T=Nothing], code, globals, locals=nothing)
```

Execute the given Python `code`.

If `globals` is a `Module`, then a persistent `dict` unique to that module is used.

By default the code runs in global scope (i.e. `locals===globals`). To use a temporary local scope, set `locals` to `()`, or to a `NamedTuple` of variables to include in the scope.

If `T==Nothing` then returns `nothing`. Otherwise `T` must be a concrete `NamedTuple` type and the corresponding items from `locals` are extracted and returned.

See also [`@pyexec`](@ref).

# Examples

The following computes `1.1+2.2` in the `Main` module as a `Float64`:

```
pyexec(@NamedTuple{ans::Float64}, "ans=x+y", Main, (x=1.1, y=2.2))  # returns (ans = 3.3,)
```

Marking variables as `global` saves them into the module scope, so that they are available in subsequent invocations:

```
pyexec("global x; x=12", Main)
pyeval(Int, "x", Main)  # returns 12
```
