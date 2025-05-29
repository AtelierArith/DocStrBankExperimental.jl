```julia
IsMouseReleasedWithDelay(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    delay
) -> Bool

```

遅延マウスリリース（非常に控えめに使用してください！）。一般的には 'delay >= io.MouseDoubleClickTime' と 'io.MouseClickedLastCount==1' テストを組み合わせて使用されます。これは非常に稀に使用されるUIのイディオムですが、一部のアプリではこれを使用しています：例えば、MS Explorerでアイコンを単一クリックして名前を変更する場合です。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1042).
