```
CallbackList(args...) <: AbstractCallback
```

Returns a callback that combines all callbacks passed as arguments and executes them in that order. Note that CallbackList uses short-circuiting and will immediately stop execution on encountering any unsuccessful exit codes, without calling the remaining callbacks.

See [`should_terminate`](@ref) for callback exit code semantics.

CallbackLists can also be constructed using the ∘ operator, where `cb1 ∘ cb2` means `cb1` is executed *after* `cb2`.

Nested CallbackLists will automatically be flattened on construction, all [`NoCallback`](@ref)s will be trimmed to save weight.
