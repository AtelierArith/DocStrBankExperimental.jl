```
get_global_achievement_percentages_for_app(gameid::Int)::Dict{String,Float16}
```

**概要**: `get_global_achievement_percentages_for_app` は、特定のゲームのグローバルな実績の概要をパーセンテージで返します。

# 引数

  * `gameid`: 実績のパーセンテージを取得するためのGameID。

# 例

```julia-repl
julia> get_global_achievement_percentages_for_app(440)
Dict{String, Float16}("TF_MAPS_DOOMSDAY_PUSH_INTO_EXHAUST" => 7.9...)
```
