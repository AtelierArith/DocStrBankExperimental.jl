```julia
IncludeItemsByIndex(
    self::Ptr{CImGui.lib.ImGuiListClipper},
    item_begin,
    item_end
)

```

Item_end is exclusive e.g. use (42, 42+1) to make item 42 never clipped.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2811).
