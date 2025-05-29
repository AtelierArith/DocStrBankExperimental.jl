```julia
MouseClick()
MouseClick(button::CImGui.lib.ImGuiMouseButton_)
MouseClick(button::CImGui.lib.ImGuiMouseButton_, ctx)

```

Register a click of `button`.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    MouseClick()                          # LMB
    MouseClick(ig.ImGuiMouseButton_Right) # RMB
end
```
