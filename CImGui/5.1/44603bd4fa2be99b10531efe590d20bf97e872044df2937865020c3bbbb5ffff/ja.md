```julia
TextColored(
    col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    fmt
)

```

ImGuiCol_Textにcolを指定してPushStyleColor(); fmt, ...を使ってText(); PopStyleColor();のショートカットです。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L545).
