```julia
GetWindowByRef(
    test_ref::Union{Int64, String}
) -> Union{Nothing, Ptr{CImGui.lib.ImGuiWindow}}
GetWindowByRef(
    test_ref::Union{Int64, String},
    ctx
) -> Union{Nothing, Ptr{CImGui.lib.ImGuiWindow}}

```

参照によって `ImGuiWindow` を取得します。ウィンドウが見つからなかった場合は `nothing` を返します。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    window_ptr = GetWindowByRef("My window")
    @show window_ptr
end
```
