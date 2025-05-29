```julia
MouseMoveToPos(x, y)
MouseMoveToPos(x, y, ctx)

```

マウスを絶対座標で指定された位置に移動します（例：[`ig.GetMousePos()`](@extref `CImGui.GetMousePos`)および[`ig.GetCursorScreenPos()`](@extref `CImGui.GetCursorScreenPos`)に一致します）。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    MouseMoveToPos(100, 100)
    MouseMoveToPos((100, 100))
    MouseMoveToPos(ig.ImVec2(100, 100))
end
```
