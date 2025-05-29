```
build_events(
    eng::Dict{String,<:Any};
    custom_events::Vector{Dict{String,Any}}=Dict{String,Any}[],
    default_switch_state::Union{PMD.SwitchState,String}=PMD.CLOSED,
    default_switch_dispatchable::Union{PMD.Dispatchable,Bool}=PMD.YES,
    default_switch_status::Union{Missing,PMD.Status,Int}=missing
)::Vector{Dict{String,Any}}
```

スイッチのデフォルト設定を持つ基本的なイベントデータ構造を作成するためのヘルパー関数です。

  * `eng::Dict{String,<:Any}` は入力ケースデータ構造です
  * `custom_events` は、`default` kwargs に基づいて自動生成されたイベントの **後に** 適用される *イベント* のベクターです
  * `default_switch_state::Union{PMD.SwitchState,String}` (デフォルト: `CLOSED`) は、すべてのスイッチに適用されるデフォルト状態のトグルです
  * `default_switch_dispatchable::Union{PMD.Dispatchable,Bool}` (デフォルト: `YES`) は、すべてのスイッチのデフォルトのディスパッチ可能性（制御可能性）のトグルです
  * `default_switch_status::Union{Missing,PMD.Status,Int}` (デフォルト: `missing`) は、すべてのスイッチのデフォルトステータス（スイッチがモデルに表示されるかどうか）を適用するためのトグルです。`missing` の場合、モデルによって与えられたステータスがデフォルトになります。
