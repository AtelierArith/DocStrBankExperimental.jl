```
@forcefun
```

Decorator for force accumulation.

Inside a method decorated with [`@forcedef`](@ref), decorating a function call with `@forcefun` indicates that the accumulator should be passed to this function.

Outside of `@forcedef`-methods, this macro has no effect and the function call is evaluated as usual.

See [`@forcedef`](@ref) for usage examples.
