```julia
IsMousePosValid() -> Bool
IsMousePosValid(
    mouse_pos::Union{Ptr{Nothing}, Ref{CImGui.lib.ImVec2}, Ref{Tuple{T, T} where T}}
) -> Bool

```

By convention we use (-FLT*MAX,-FLT*MAX) to denote that there is no mouse available.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1045).
