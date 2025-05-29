```julia
GetMouseClickedCount(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Int32

```

クリックが発生した時点での連続したマウスクリックの回数を返します（それ以外は0）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1043).
