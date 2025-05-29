```
with_context(f, var1 => value1, var2 => value2, ...)
with_context(f, pairs)
```

Run `f` in a context with given values set to the context variables.  Variables specified in this form are rolled back to the original value when `with_context` returns.  It act like a dynamically scoped `let`.  If `nothing` is passed as a value, corresponding context variable is cleared; i.e., it is unassigned or takes the default value.  Use `Some(value)` to set `value` if `value` can be `nothing`.

```
with_context(f, nothing)
```

Run `f` in a new empty context.  All variables are rewind to the original values when `with_context` returns.

Note that

```julia
var2[] = value2
with_context(var1 => value1) do
    @show var2[]  # shows value2
    var3[] = value3
end
@show var3[]  # shows value3
```

and

```julia
var2[] = value2
with_context(nothing) do
    var1[] = value1
    @show var2[]  # shows default (or throws)
    var3[] = value3
end
@show var3[]  # does not show value3
```

are not equivalent.
