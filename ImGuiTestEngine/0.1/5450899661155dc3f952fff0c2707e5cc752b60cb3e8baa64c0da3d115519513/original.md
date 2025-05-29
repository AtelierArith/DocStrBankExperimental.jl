```julia
mutable struct Engine
```

Represents a test engine context. This a wrapper around the upstream `ImGuiTestEngine` type. Don't create it yourself, use [`CreateContext()`](@ref).
