```julia
ShowStyleEditor()
ShowStyleEditor(
    ref::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiStyle}}
)

```

スタイルエディタブロックを追加します（ウィンドウではありません）。比較、元に戻す、保存するために参照ImGuiStyle構造体を渡すことができます（そうでない場合はデフォルトスタイルが使用されます）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L354).
