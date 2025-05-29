```
get_batcontext()::BATContext
get_batcontext(obj)::BATContext
```

Gets resp. sets the default computational context for BAT.

Will create and set a new default context if none exists.

Note: `get_batcontext()` does not have a stable return type. Code that needs type stability should pass a context to algorithms explicitly. BAT algorithms that call other algorithms must forward their context automatically, so context is always type stable within nested BAT algorithms.

See [`BATContext`](@ref) and [`set_batcontext`](@ref).
