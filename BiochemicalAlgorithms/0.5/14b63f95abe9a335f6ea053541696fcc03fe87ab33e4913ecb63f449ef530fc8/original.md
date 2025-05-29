```
struct SystemComponentTable{T, C <: AbstractSystemComponent{T}} <: AbstractSystemComponentTable{T}
```

Tables.jl-compatible system component table for a specific `System{T}` and system component `C` (e.g., `Atom{T}`, `Bond{T}`, etc.).
