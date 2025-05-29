```
@force expr
```

Decorator for force accumulation.

Inside a method decorated with [`@forcedef`](@ref), decorating an expression with `@force` indicates that the result of the expression should be pushed to the accumulator.

Outside of `@forcedef`-methods, `expr` is not evaluated.

See [`@forcedef`](@ref) for usage examples.
