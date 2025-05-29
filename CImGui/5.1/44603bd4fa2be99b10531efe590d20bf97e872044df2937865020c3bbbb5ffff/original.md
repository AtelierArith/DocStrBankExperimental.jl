```julia
TextColored(
    col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    fmt
)

```

Shortcut for PushStyleColor(ImGuiCol_Text, col); Text(fmt, ...); PopStyleColor();.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L545).
