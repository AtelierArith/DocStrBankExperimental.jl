```
sorted_arguments(x::T)
```

Returns the arguments to the function call in a function call expression, in a **sorted fashion**. `iscall(x)` must be true as a precondition. Analogous to `arguments`,  but ensures that the operation is deterministic and always returns  the arguments in the order they are stored.

By default, this redirects to `arguments`, therefore implementing  it is optional.
