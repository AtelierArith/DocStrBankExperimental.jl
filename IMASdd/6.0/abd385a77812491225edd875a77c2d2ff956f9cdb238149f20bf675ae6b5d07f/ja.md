```
get_timeslice(@nospecialize(ids::IDS), time0::Float64=global_time(ids), scheme::Symbol=:constant; slice_pulse_schedule::Bool=true)
```

指定された `time0` でデータを返します（デフォルトでは global_time で）。

データは、最も近い因果的時間点を使用して、時間依存の構造体の配列から選択されます。

データは、次の可能なスキーム `[:constant, :linear, :quadratic, :cubic, :pchip, :lagrange]` を使用して、時間依存の配列から選択されます。
