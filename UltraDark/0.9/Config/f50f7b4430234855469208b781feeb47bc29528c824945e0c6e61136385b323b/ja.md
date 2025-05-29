```julia
struct TimeStepOptions
```

時間ステップのサイズと計算を制御するオプションを含む構造体。

参照: [`SimulationConfig`](@ref)

# 例

```jldoctest
julia> using UltraDark

julia> TimeStepOptions()
TimeStepOptions(10, 1.0)
```

# フィールド

  * `update_period::Int64`: 時間ステップが更新される前に取られるステップの数を制御します
  * `multiplier::Float64`: 計算された最大時間ステップに定数を掛けます
