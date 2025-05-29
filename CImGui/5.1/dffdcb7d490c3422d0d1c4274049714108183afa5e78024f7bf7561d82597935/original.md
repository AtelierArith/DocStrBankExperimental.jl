```julia
AddDrawCmd(self::Ptr{CImGui.lib.ImDrawList})

```

This is useful if you need to forcefully create a new draw call (to allow for dependent rendering / blending). Otherwise primitives are merged into the same draw-call as much as possible.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3290).
