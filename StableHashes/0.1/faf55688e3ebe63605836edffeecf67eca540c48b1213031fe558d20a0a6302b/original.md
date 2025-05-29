```
shash(x[, h::UInt])
```

Compute an integer shash code such that `isequal(x,y)` implies `shash(x)==shash(y)`. The optional second argument `h` is a shash code to be mixed with the result.

New types should implement the 2-argument form, typically by calling the 2-argument `shash` method recursively in order to mix shashes of the contents with each other (and with `h`). Typically, any type that implements `shash` should also implement its own `==` (hence `isequal`) to guarantee the property mentioned above. Types supporting subtraction (operator `-`) should also implement [`widen`](@ref), which is required to shash values inside heterogeneous arrays.
