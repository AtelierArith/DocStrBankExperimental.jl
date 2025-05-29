```julia
IsKeyChordPressed(key_chord::Integer) -> Bool

```

キーコード（修飾キー + キー）が押されたかどうかを確認します。例えば、'ImGuiMod*Ctrl | ImGuiKey*S'をキーコードとして渡すことができます。これはルーティングやフォーカスチェックを行わないため、代わりにShortcut()関数の使用を検討してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1003).
