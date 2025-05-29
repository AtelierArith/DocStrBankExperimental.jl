```julia
TableSetColumnEnabled(column_n, v)

```

ユーザーがアクセス可能な列の有効/無効状態を変更します。列を非表示にするにはfalseに設定します。ユーザーはコンテキストメニューを使用して自分でこれを変更できます（ヘッダーを右クリックするか、ImGuiTableFlags_ContextMenuInBodyを使用して列の本体を右クリックします）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L856).
