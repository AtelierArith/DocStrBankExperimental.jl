```julia
AddKeyEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    key::CImGui.lib.ImGuiKey,
    down
)

```

新しいキーの押下/解放イベントをキューに追加します。キーは「変換」されるべきです（つまり、一般的に ImGuiKey_A はエンドユーザーが 'A' 文字を発生させるために使用するキーに対応します）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2438).
