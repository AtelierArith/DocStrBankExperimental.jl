```
@kernel config function f(args) end
```

This allows for two different configurations:

1. `cpu={true, false}`: Disables code-generation of the CPU function. This relaxes semantics such that KernelAbstractions primitives can be used in non-kernel functions.
2. `inbounds={false, true}`: Enables a forced `@inbounds` macro around the function definition in the case the user is using too many `@inbounds` already in their kernel. Note that this can lead to incorrect results, crashes, etc and is fundamentally unsafe. Be careful!
3. `unsafe_indices={false, true}`: Disables the implicit validation of indices, users must avoid `@index(Global)`.

  * [`@context`](@ref)

!!! warn
    This is an experimental feature.

