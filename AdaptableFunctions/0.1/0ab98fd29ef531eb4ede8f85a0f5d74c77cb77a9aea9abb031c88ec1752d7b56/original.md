```
adapt_to_input(f::F, example_input::T) where {F,T}
```

Generates a function that performs the same operation as `f`, but this is optimized/specialized for the type and size of `example_input` and the computing device `example_input` resides on.

Returns the optimized/specialized version of f, or [`UnadaptedFunction{F,T}(f)`](@ref) if this is not possible.
