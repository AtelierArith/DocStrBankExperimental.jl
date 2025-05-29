```julia
MouseClick()
MouseClick(button::CImGui.lib.ImGuiMouseButton_)
MouseClick(button::CImGui.lib.ImGuiMouseButton_, ctx)

```

`button`のクリックを登録します。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    MouseClick()                          # LMB
    MouseClick(ig.ImGuiMouseButton_Right) # RMB
end
```
