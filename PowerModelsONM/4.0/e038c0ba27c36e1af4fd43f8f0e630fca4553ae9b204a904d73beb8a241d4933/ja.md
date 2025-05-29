```
get_timestep_inverter_states(optimal_switching_results::Dict{String,<:Any})::Vector{Dict{String,Any}}
```

`optimal_switching_results`から各時刻の各発電オブジェクトの'inverter'状態を取得します。インバータ状態が利用できない場合は、デフォルトで`GRID_FORMING`になります。
