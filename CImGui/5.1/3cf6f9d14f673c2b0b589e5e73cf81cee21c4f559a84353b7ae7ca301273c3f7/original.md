```julia
GetVoidPtrRef(
    self::Ptr{CImGui.lib.ImGuiStorage},
    key::Integer
) -> Ptr{Ptr{Nothing}}
GetVoidPtrRef(
    self::Ptr{CImGui.lib.ImGuiStorage},
    key::Integer,
    default_val
) -> Ptr{Ptr{Nothing}}

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2757).
