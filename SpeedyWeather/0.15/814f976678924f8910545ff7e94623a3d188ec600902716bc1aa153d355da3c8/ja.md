```julia
tree(S; modules, with_size, kwargs...)

```

S内のフィールドと、モジュール引数内で定義されているこれらのフィールド内のフィールドのツリーを作成します（デフォルトはSpeedyWeather）。他のキーワード引数は `max_level::Integer=10`、`with_types::Bool=false` または `with_size::Bool=false` です。
