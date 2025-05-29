```julia
MouseMoveToPos(x, y)
MouseMoveToPos(x, y, ctx)

```

Move the mouse to the given position in absolute coordinates (e.g. matching [`ig.GetMousePos()`](@extref `CImGui.GetMousePos`) and [`ig.GetCursorScreenPos()`](@extref `CImGui.GetCursorScreenPos`)).

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    MouseMoveToPos(100, 100)
    MouseMoveToPos((100, 100))
    MouseMoveToPos(ig.ImVec2(100, 100))
end
```
