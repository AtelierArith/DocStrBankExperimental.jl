```julia
SetStateStorage(
    storage::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiStorage}}
)

```

Replace current window storage with our own (if you want to manipulate it yourself, typically clear subsection of it).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L984).
