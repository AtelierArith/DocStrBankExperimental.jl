```julia
struct CxxPtr{ImGuiTestEngine.lib.ImGuiTestContext} <: CxxWrap.CxxWrapCore.CxxBaseRef{ImGuiTestEngine.lib.ImGuiTestContext}
```

This is a reference to a `ImGuiTestContext`. It cannot be created directly, instead the context will be passed to the `GuiFunc` and `TestFunc` functions of an [`ImGuiTest`](@ref).

!!! danger
    This a memory-unsafe type, only use it while the engine is alive.

