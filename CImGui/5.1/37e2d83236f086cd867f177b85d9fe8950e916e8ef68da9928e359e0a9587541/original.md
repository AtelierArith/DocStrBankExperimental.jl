```julia
GetDrawData() -> Ptr{CImGui.lib.ImDrawData}

```

Valid after Render() and until the next call to NewFrame(). this is what you have to render.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L346).
