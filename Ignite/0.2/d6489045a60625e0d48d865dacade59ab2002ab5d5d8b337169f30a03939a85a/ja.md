```julia
struct State <: AbstractDict{Symbol, Any}
```

エンジンの現在の状態。

`State` は `DefaultOrderedDict{Symbol, Any, Nothing}` の軽量ラッパーで、以下のキーを持っています：

  * `:iteration`: 現在のイテレーション、1から始まります。
  * `:epoch`: 現在のエポック、1から始まります。
  * `:max_epochs`: 実行するエポックの数。
  * `:epoch_length`: エポックごとに処理されるバッチの数。
  * `:output`: 単一のイテレーション後の `process_function` の出力。
  * `:last_event`: 最後に発生したイベント。
  * `:counters`: 発火イベントのカウンターを持つ `DefaultOrderedDict{AbstractFiringEvent, Int, Int}(0)`。
  * `:times`: 発火イベントキーで取得された合計およびエポックごとの時間を持つ `OrderedDict{AbstractFiringEvent, Float64}()`。

フィールドは `getproperty` と `setproperty!` を使用してアクセスおよび変更できます。例えば、`engine.state.iteration` を使用して現在のイテレーションにアクセスでき、`engine.state.new_field = value` を使用して `value` を後で使用するために保存できます（例：イベントハンドラーによって）。
