```julia
TextWrapped(fmt)

```

PushTextWrapPos(0.0f); Text(fmt, ...); PopTextWrapPos(); のショートカットです。ウィンドウの幅を拡張する他のウィジェットがない場合、自動サイズ変更ウィンドウでは機能しないことに注意してください。SetNextWindowSize()を使用してサイズを設定する必要があるかもしれません。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L549).
