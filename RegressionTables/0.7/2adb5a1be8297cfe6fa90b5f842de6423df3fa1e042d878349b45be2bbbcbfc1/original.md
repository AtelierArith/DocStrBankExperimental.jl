```
abstract type AbstractRenderType end
```

The generic top level type for render types. Most defaults are set here unless there is a reason it needs to be set at a lower level. Subtypes are still abstract types and include [`AbstractAscii`](@ref), [`AbstractLatex`](@ref), and [`AbstractHtml`](@ref).
