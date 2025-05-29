```julia
ShowStyleEditor()
ShowStyleEditor(
    ref::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiStyle}}
)

```

Add style editor block (not a window). you can pass in a reference ImGuiStyle structure to compare to, revert to and save to (else it uses the default style).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L354).
