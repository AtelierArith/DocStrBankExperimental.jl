```
YourAgentType <: AbstractAgent
```

Agents participating in Agents.jl simulations are instances of user-defined types that are subtypes of `AbstractAgent`.

Your agent type(s) **must have** the `id::Int` field as first field. If any space is used (see [Available spaces](@ref available_spaces)), a `pos` field of appropriate type is also mandatory. The core model structure, and each space, may also require additional fields that may, or may not, be communicated as part of the public API.

The [`@agent`](@ref) macro ensures that all of these constrains are in place and hence it is the **the only supported way to create agent types**.
