```julia
GetWindowByRef(
    test_ref::Union{Int64, String}
) -> Union{Nothing, Ptr{CImGui.lib.ImGuiWindow}}
GetWindowByRef(
    test_ref::Union{Int64, String},
    ctx
) -> Union{Nothing, Ptr{CImGui.lib.ImGuiWindow}}

```

Retrieve a `ImGuiWindow` by reference. This will return `nothing` if the window was not found.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    window_ptr = GetWindowByRef("My window")
    @show window_ptr
end
```
