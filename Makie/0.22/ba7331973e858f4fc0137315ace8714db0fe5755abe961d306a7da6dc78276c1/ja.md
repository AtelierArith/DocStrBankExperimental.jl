この構造体は、シーンに関連するイベントを監視するためのアクセス可能な `Observable` を提供します。

`Observable` に作用する関数は、イベントを消費する場合に `Consume()` を返さなければなりません。イベントが消費されると、他のオブザーバ関数はトリガーされません。関数が実行される順序は、`on` の `priority` キーワード（デフォルトは 0）を介して制御できます。

例:

```julia
on(events(scene).mousebutton, priority = 20) do event
    if is_correct_event(event)
        do_something()
        return Consume()
    end
    return
end
```

## フィールド

  * `window_area::Observables.Observable{GeometryBasics.HyperRectangle{2, Int64}}`: ピクセル単位のウィンドウの領域を `Rect2` として表します。
  * `window_dpi::Observables.Observable{Float64}`: ウィンドウの DPI 解像度を `Float64` として表します。
  * `window_open::Observables.Observable{Bool}`: ウィンドウの状態（開いている => true, 閉じている => false）。
  * `mousebutton::Observables.Observable{Makie.MouseButtonEvent}`: 最も最近トリガーされた `MouseButtonEvent`。関連する `event.button` と `event.action`（押す/離す）を含みます。

    参照: [`ispressed`](@ref)。
  * `mousebuttonstate::Set{Makie.Mouse.Button}`: 現在押されているすべてのマウスボタンのセット。
  * `mouseposition::Observables.Observable{Tuple{Float64, Float64}}`: マウスの位置を `NTuple{2, Float64}` として表します。イベントポール/フレームごとに一度更新されます。
  * `scroll::Observables.Observable{Tuple{Float64, Float64}}`: スクロールの方向。
  * `keyboardbutton::Observables.Observable{Makie.KeyEvent}`: 最も最近トリガーされた `KeyEvent`。関連する `event.key` と `event.action`（押す/繰り返す/離す）を含みます。

    参照: [`ispressed`](@ref)。
  * `keyboardstate::Set{Makie.Keyboard.Button}`: 現在押されているすべてのキーを含みます。
  * `unicode_input::Observables.Observable{Char}`: 最後に入力された文字を含みます。
  * `dropped_files::Observables.Observable{Vector{String}}`: シーンにドラッグされたファイルのパスのリストを含みます。
  * `hasfocus::Observables.Observable{Bool}`: シーンウィンドウがフォーカスされているかどうか。
  * `entered_window::Observables.Observable{Bool}`: マウスがウィンドウ内にいるかどうか。
  * `tick::Observables.Observable{Makie.Tick}`: 新しいフレームが要求されるたびに `tick` がトリガーされます。つまり、通常のレンダリング中（レンダーループが一時停止していても）や、`save` または `record` のために画像が生成されるときです。Tick には以下が含まれます：

      * `state` は、tick を引き起こした原因を特定します（Makie.TickState を参照）。
      * `count` は、各 tick ごとに増加します。
      * `time` は、画面が作成されてからの総時間です。
      * `delta_time` は、最後のフレームからの時間です。
