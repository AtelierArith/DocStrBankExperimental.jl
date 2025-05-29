```julia
IncludeItemsByIndex(
    self::Ptr{CImGui.lib.ImGuiListClipper},
    item_begin,
    item_end
)

```

item_endは排他的です。例えば、(42, 42+1)を使用してアイテム42がクリップされないようにします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2811).
