```julia
SetRef(window::Ptr{CImGui.lib.ImGuiWindow})
SetRef(window::Ptr{CImGui.lib.ImGuiWindow}, ctx)

```

Same as [`SetRef(::TestRef)`](@ref), except it takes an explicit window to set a reference to.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    window = GetWindowByRef("Window")
    SetRef(window)
end
```
