```julia
SetRef(window::Ptr{CImGui.lib.ImGuiWindow})
SetRef(window::Ptr{CImGui.lib.ImGuiWindow}, ctx)

```

[`SetRef(::TestRef)`](@ref) と同様ですが、参照を設定するための明示的なウィンドウを取ります。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    window = GetWindowByRef("Window")
    SetRef(window)
end
```
