```
apply!(sim, func, call, read, write; add_existing)
```

Call [`apply!`](@ref) with a copy of the simulation so that the state of `sim` itself is not changed.

Can be very useful during development, especially if Vahana is used in the REPL. However, for performance reasons, this function should not be used in the final code.

Returns the copy of the simulation.

See also [`apply!`](@ref)
