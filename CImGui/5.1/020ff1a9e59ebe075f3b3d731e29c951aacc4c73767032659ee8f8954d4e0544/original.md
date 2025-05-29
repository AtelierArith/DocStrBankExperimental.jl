```julia
GetColorU32(
    col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T}
) -> UInt32

```

Retrieve given color with style alpha applied, packed as a 32-bit value suitable for ImDrawList.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L479).
