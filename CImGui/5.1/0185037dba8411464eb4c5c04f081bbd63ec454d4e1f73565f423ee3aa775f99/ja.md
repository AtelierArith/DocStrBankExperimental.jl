```julia
ImageButton(
    str_id,
    user_texture_id::UInt64,
    image_size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
ImageButton(
    str_id,
    user_texture_id::UInt64,
    image_size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv0::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
ImageButton(
    str_id,
    user_texture_id::UInt64,
    image_size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv0::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv1::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
ImageButton(
    str_id,
    user_texture_id::UInt64,
    image_size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv0::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv1::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    bg_col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T}
) -> Bool
ImageButton(
    str_id,
    user_texture_id::UInt64,
    image_size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv0::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv1::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    bg_col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    tint_col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L580).
