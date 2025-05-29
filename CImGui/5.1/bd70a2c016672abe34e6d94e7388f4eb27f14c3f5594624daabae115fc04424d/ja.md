```julia
SliderFloat(label, v, v_min, v_max) -> Bool
SliderFloat(label, v, v_min, v_max, format) -> Bool
SliderFloat(
    label,
    v,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

formatを調整して、スライダー内のラベルや単位表示のために値にプレフィックスまたはサフィックスを装飾します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L622).
