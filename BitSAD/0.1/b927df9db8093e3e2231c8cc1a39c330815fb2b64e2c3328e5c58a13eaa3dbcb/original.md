```
simulatable(f, args...)
```

Return a simulatable variation of `f(args...)` that emulates the bit-level operations for [`SBitstream`](#) variables. The returned function, call it `sim`, can be called via `sim(f, args...)`.

This is done by recursively tracing the execution of `f(args...)` then replacing each primitive simulatable operation with a simulatable operator.
