```julia
IsItemToggledSelection() -> Bool

```

最後のアイテム選択状態は切り替えられましたか？これは、EndMultiSelect()に到達する*前に*アイテムごとの情報が必要な場合に便利です。クリッピングを正しく処理するために、トグル*イベント*のみを返します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L702).
