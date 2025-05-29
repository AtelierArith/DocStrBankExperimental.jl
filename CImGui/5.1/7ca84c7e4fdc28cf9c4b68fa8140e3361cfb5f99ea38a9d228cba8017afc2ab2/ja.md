```julia
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    flags::Union{CImGui.lib.ImGuiTreeNodeFlags_, Integer}
) -> Bool

```

'true'を返す場合、ヘッダーは開いています。IDスタックにインデントやプッシュは行いません。ユーザーはTreePop()を呼び出す必要はありません。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L681).
