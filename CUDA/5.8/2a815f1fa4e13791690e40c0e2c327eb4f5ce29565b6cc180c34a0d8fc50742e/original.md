```
context!(ctx::CuContext)
context!(ctx::CuContext) do ... end
```

Bind the current host thread to the context `ctx`. Returns the previously-bound context. If used with do-block syntax, the change is only temporary.

Note that the contexts used with this call should be previously acquired by calling [`context`](@ref), and not arbitrary contexts created by calling the `CuContext` constructor.
