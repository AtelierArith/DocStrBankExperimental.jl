```
parse_events(
    raw_events::Vector{<:Dict{String,<:Any}},
    mn_data::Dict{String,<:Any}
)::Dict{String,Any}
```

`raw_events`を、例えばJSONから読み込まれた形式であるVector{Dict}から、マルチネットワークデータ構造に簡単にマージ（適用）できるように、内部データ構造に変換します。

指定されたタイムステップから正しいサブネットワークを見つけるために、マルチネットワークデータ構造の「mn_lookup」を使用しようとします。

## スイッチイベント

`source_id`から正しいスイッチIDを見つけます。すなわち、ソースファイルからのasset*type.nameで、スイッチの場合は`line.name`となり、ネイティブENGINEERINGスイッチIDの下で`event*data`に定義されたプロパティを含むデータ構造を作成します。

## 故障イベント

故障を隔離するためにOPENにする必要がある適切なスイッチを見つけ、それらを無効にし、すなわち`dispatchable=false`に設定します。これは故障の`duration`（ミリ秒単位）で指定された期間中です。

故障が終了した後、次のタイムステップが存在する場合はスイッチを再度有効にし、すなわち`dispatchable=true`に設定しますが、スイッチを自動的にCLOSEDに戻すことはありません。これはアルゴリズム[`optimize_switches`](@ref optimize_switches)が決定することです。
