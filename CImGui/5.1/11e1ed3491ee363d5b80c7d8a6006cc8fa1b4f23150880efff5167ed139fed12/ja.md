```julia
OpenPopup(str_id::Union{Ptr{Int8}, Ptr{Nothing}, String})
OpenPopup(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String},
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
)

```

ポップアップを開いているとマークするための呼び出し（毎フレーム呼び出さないでください！）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L783).
