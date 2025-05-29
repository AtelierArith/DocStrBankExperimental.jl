```julia
IsItemDeactivatedAfterEdit() -> Bool

```

最後のアイテムは非アクティブにされ、アクティブなときに値が変更されましたか？（例：スライダー/ドラッグが移動した）。連続編集を必要とするウィジェットのための元に戻す/やり直すパターンに便利です。すでに選択されているアイテムをクリックしても、Combo()/ListBox()/Selectable()などの一部のウィジェットはtrueを返すため、偽陽性が発生する可能性があることに注意してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L957).
