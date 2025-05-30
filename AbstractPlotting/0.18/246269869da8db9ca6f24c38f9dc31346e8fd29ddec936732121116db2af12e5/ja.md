この構造体は、シーンに関連するイベントを監視するためのアクセス可能な `PriorityObservable` を提供します。

`PriorityObservable` に作用する関数は、イベントを消費する場合は true を返し、消費しない場合は false を返さなければなりません。イベントが消費されると、他のオブザーバ関数はトリガーされません。関数が実行される順序は、`on` の `priority` キーワード（デフォルトは 0）を介して制御できます。

例:

```
on(events(scene).mousebutton, priority = Int8(20)) do event
    if is_correct_event(event)
        do_something()
        return true
    end
    return false
end
```

## フィールド

  * `window_area::AbstractPlotting.PriorityObservable{GeometryBasics.HyperRectangle{2, Int64}}`: ピクセル単位のウィンドウの領域、`Rect2D` として。
  * `window_dpi::AbstractPlotting.PriorityObservable{Float64}`: ウィンドウの DPI 解像度、`Float64` として。
  * `window_open::AbstractPlotting.PriorityObservable{Bool}`: ウィンドウの状態（開いている => true、閉じている => false）。
  * `mousebutton::AbstractPlotting.PriorityObservable{AbstractPlotting.MouseButtonEvent}`: 最も最近トリガーされた `MouseButtonEvent`。関連する `event.button` と `event.action`（押す/放す）を含みます。

    参照: [`ispressed`](@ref)。
  * `mousebuttonstate::Set{AbstractPlotting.Mouse.Button}`: 現在押されているすべてのマウスボタンのセット。
  * `mouseposition::AbstractPlotting.PriorityObservable{Tuple{Float64, Float64}}`: マウスの位置を `NTuple{2, Float64}` として。イベントポール/フレームごとに一度更新されます。
  * `scroll::AbstractPlotting.PriorityObservable{Tuple{Float64, Float64}}`: スクロールの方向。
  * `keyboardbutton::AbstractPlotting.PriorityObservable{AbstractPlotting.KeyEvent}`: 最も最近トリガーされた `KeyEvent`。関連する `event.key` と `event.action`（押す/繰り返す/放す）を含みます。

    参照: [`ispressed`](@ref)。
  * `keyboardstate::Set{AbstractPlotting.Keyboard.Button}`: 現在押されているすべてのキーを含みます。
  * `unicode_input::AbstractPlotting.PriorityObservable{Char}`: 最後に入力された文字を含みます。
  * `dropped_files::AbstractPlotting.PriorityObservable{Vector{String}}`: シーンにドラッグされたファイルのファイルパスのリストを含みます。
  * `hasfocus::AbstractPlotting.PriorityObservable{Bool}`: シーンウィンドウがフォーカスされているかどうか。
  * `entered_window::AbstractPlotting.PriorityObservable{Bool}`: マウスがウィンドウ内にいるかどうか。
