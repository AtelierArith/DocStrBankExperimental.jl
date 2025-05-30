```
@code_typed
```

Evaluates the arguments to the function or macro call, determines their types, and calls [`code_typed`](@ref) on the resulting expression. Use the optional argument `optimize` with

```
@code_typed optimize=true foo(x)
```

to control whether additional optimizations, such as inlining, are also applied.
