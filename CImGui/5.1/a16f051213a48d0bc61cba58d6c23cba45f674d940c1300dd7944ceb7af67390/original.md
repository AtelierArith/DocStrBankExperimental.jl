```julia
DeIndexAllBuffers(self::Ptr{CImGui.lib.ImDrawData})

```

Helper to convert all buffers from indexed to non-indexed, in case you cannot render indexed. Note: this is slow and most likely a waste of resources. Always prefer indexed rendering!

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3355).
