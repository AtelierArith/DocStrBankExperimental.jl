```julia
GetStyleColorVec4(
    idx::Union{CImGui.lib.ImGuiCol_, Integer}
) -> Ptr{CImGui.lib.ImVec4}

```

ImGuiStyle構造体に保存されているスタイルカラーを取得します。PushStyleColor()にフィードバックするために使用するか、そうでなければGetColorU32()を使用してスタイルアルファが組み込まれたスタイルカラーを取得します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L481).
