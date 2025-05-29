イベントキューは、アプリケーションによって処理されるイベントを保持するためのものです。

イベントキューはウィンドウマネージャにバインドされており、そのウィンドウマネージャから送信される低レベルイベントの通知に応じて満たされます。イベントキューには、高レベルイベントのみが記録され、これらは通常アプリケーションでの使用に適しています。

イベントキューは無限に反復可能であり、受信した[`Event`](@ref)を返します。イベントが利用できない場合、キューは約1ミリ秒のスリープ状態に入るか（`sleep = true`の場合）、各反復でスピンしながら待機します。

したがって、イベントキューを反復する任意のタスクは、Julia 1.9以降のインタラクティブスレッドを使用してスケジュールされる良い候補です。

また、イベントキューは手動で[`collect_events!`](@ref)を使用して満たし、`Base.isempty`および`Base.popfirst!`を使用して処理することもできます。

パラメータ`record_history`は、処理されたすべてのイベント（反復または手動の`Base.popfirst!`による）を保存するために`true`に設定できます。ウィンドウマネージャの実装は、保存されたイベントの保存と再生を可能にするために[`save_history`](@ref)および[`replay_history`](@ref)を拡張することがあります。`record_history`は、[`save_history`](@ref)が機能するために`true`に設定する必要があることに注意してください。

```julia
struct EventQueue{WM<:WindowAbstractions.AbstractWindowManager, W<:WindowAbstractions.AbstractWindow}
```

  * `wm::WindowAbstractions.AbstractWindowManager`
  * `events::Array{WindowAbstractions.Event{W}, 1} where W<:WindowAbstractions.AbstractWindow`
  * `history::Array{WindowAbstractions.Event{W}, 1} where W<:WindowAbstractions.AbstractWindow`
  * `sleep::Bool`
  * `record_history::Bool`
