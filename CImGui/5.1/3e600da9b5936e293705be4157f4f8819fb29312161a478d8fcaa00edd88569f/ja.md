```julia
AddMouseViewportEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    id::Integer
)

```

マウスがホバーされたビューポートをキューに追加します。これを呼び出すには、バックエンドがImGuiBackendFlags_HasMouseHoveredViewportを設定する必要があります（マルチビューポートサポートのため）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2444).
