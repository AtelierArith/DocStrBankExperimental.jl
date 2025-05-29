```julia
tree(
    M::SpeedyWeather.AbstractModel;
    modules,
    with_size,
    kwargs...
)

```

モデル内のフィールドと、モジュール引数内で定義されているフィールド内のフィールドのツリーを作成します（デフォルトはSpeedyWeather）。他のキーワード引数は `max_level::Integer=10`、`with_types::Bool=false` または `with_size::Bool=false` です。
