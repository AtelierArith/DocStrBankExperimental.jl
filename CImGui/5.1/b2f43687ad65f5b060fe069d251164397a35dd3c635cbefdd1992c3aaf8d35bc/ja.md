```julia
SetDragDropPayload(type, data, sz) -> Bool
SetDragDropPayload(
    type,
    data,
    sz,
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
) -> Bool

```

タイプは最大32文字のユーザー定義の文字列です。'_'で始まる文字列は、dear imguiの内部タイプのために予約されています。データはimguiによってコピーされ保持されます。ペイロードが受け入れられたときにtrueを返します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L916).
