```julia
CalcTextSizeA(
    self::Ptr{CImGui.lib.ImFont},
    size,
    max_width,
    wrap_width,
    text_begin
) -> CImGui.lib.ImVec2
CalcTextSizeA(
    self::Ptr{CImGui.lib.ImFont},
    size,
    max_width,
    wrap_width,
    text_begin,
    text_end
) -> CImGui.lib.ImVec2
CalcTextSizeA(
    self::Ptr{CImGui.lib.ImFont},
    size,
    max_width,
    wrap_width,
    text_begin,
    text_end,
    remaining
) -> CImGui.lib.ImVec2

```

Utf8.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3605).
