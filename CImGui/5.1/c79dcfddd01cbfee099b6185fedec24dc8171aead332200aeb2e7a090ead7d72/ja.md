```julia
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_visible::Union{Ptr{Nothing}, Ref{Bool}}
) -> Bool
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_visible::Union{Ptr{Nothing}, Ref{Bool}},
    flags::Union{CImGui.lib.ImGuiTreeNodeFlags_, Integer}
) -> Bool

```

'p*visible != NULL' の場合: '*p*visible==true' であれば、ヘッダーの右上に小さな閉じるボタンを表示し、クリックするとブール値が false に設定されます。'*p_visible==false' の場合は、ヘッダーを表示しません。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L682).
