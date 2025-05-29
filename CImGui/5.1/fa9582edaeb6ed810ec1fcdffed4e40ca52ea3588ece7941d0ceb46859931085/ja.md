```julia
RenderText(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    text
)
RenderText(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    text,
    text_end
)
RenderText(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    text,
    text_end,
    hide_text_after_hash
)

```

!!! 警告     この関数は内部的なものであり、将来的に変更される可能性があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3694).
