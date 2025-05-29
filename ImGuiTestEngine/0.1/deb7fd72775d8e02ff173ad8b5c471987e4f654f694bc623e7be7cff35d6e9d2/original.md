```
@imcheck expr
```

A port of the upstream `IM_CHECK()` macro. Like the upstream macro, this will return early from the calling function if `expr` evaluates to `false`. Prefer using it over `@test` because it will register test results with the test engine, which can be convenient if you're using the built-in test engine window (see [`ShowTestEngineWindows()`](@ref)).

`@imcheck` hooks into `@testset`'s by default, so a failure will be recorded with your Julia `Test` tests as well as with the test engine. If this is not wanted it can be disabled by passing `jltest=false`.

!!! note
    A limitation of the current implementation is that nicely parsing the expression, e.g. to display both arguments of an equality, is not supported.


# Examples

```julia
engine = te.CreateContext()
@register_test(engine, "foo", "bar") do ctx
    # This record the result with `Test` as well as the test engine
    @imcheck false

    # This will only record the result with the test engine
    @imcheck false jltest=false
end
```
