```
dispatch_state_decorator(s::AbstractManoptSolverState)
```

Indicate internally, whether an [`AbstractManoptSolverState`](@ref) `s` is of decorating type, and stores (encapsulates) a state in itself, by default in the field `s.state`.

Decorators indicate this by returning `Val{true}` for further dispatch.

The default is `Val{false}`, so by default a state is not decorated.
