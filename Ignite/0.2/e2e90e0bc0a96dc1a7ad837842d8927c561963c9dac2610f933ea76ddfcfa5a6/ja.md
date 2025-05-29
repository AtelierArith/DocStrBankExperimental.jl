```julia
mutable struct Engine{P}
```

`Engine`構造体は[`Ignite.run!`](@ref)を使用して実行されます。`engine = Engine(process_function; kwargs...)`を介して構築でき、プロセス関数は2つの引数を取ります：親`engine`とデータのバッチです。

フィールド:

  * `process_function::Any`: 単一のデータバッチを処理し、出力を返す関数。
  * `state::Ignite.State`: エンジンの現在の状態を保持するオブジェクト。
  * `event_handlers::Vector{Ignite.EventHandler}`: エンジンが実行中に特定のポイントで呼び出されるイベントハンドラーのリスト。
  * `logger::Union{Nothing, Base.CoreLogging.AbstractLogger}`: オプションのロガー；`nothing`の場合、`current_logger()`が使用されます。
  * `timer::TimerOutputs.TimerOutput`: 内部タイマー。イベントのタイミングを記録するために`TimerOutputs`と共に使用できます。
  * `should_terminate::Bool`: エンジンが実行を停止すべきかどうかを示すフラグ。
  * `exception::Union{Nothing, Exception}`: トレーニング中にスローされた例外。
