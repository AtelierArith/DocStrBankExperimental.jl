```julia
GetStyleColorVec4(
    idx::Union{CImGui.lib.ImGuiCol_, Integer}
) -> Ptr{CImGui.lib.ImVec4}

```

Retrieve style color as stored in ImGuiStyle structure. use to feed back into PushStyleColor(), otherwise use GetColorU32() to get style color with style alpha baked in.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L481).
