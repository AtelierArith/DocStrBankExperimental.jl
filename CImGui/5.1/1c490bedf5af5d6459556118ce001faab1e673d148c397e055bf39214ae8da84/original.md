```julia
GetColorU32(
    idx::Union{CImGui.lib.ImGuiCol_, Integer}
) -> UInt32
GetColorU32(
    idx::Union{CImGui.lib.ImGuiCol_, Integer},
    alpha_mul::Real
) -> UInt32

```

Retrieve given style color with style alpha applied and optional extra alpha multiplier, packed as a 32-bit value suitable for ImDrawList.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L478).
