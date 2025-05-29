```julia
GetID(
    self::Ptr{CImGui.lib.ImGuiWindow},
    str::Union{Ptr{Int8}, String}
) -> UInt32
GetID(
    self::Ptr{CImGui.lib.ImGuiWindow},
    str::Union{Ptr{Int8}, String},
    str_end::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> UInt32

```

!!! warning
    This function is internal, it may change in the future.


[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L2821).
