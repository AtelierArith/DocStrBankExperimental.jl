```
prepare_transmission_data!(
    data::Dict{String,<:Any};
    flat_start::Bool=false,
    neglect_line_charging::Bool=false,
    neglect_transformer::Bool=false,
    zero_gen_setpoints::Bool=false
)
```

送電データセットに対して一般的なデータ準備タスクを実行するためのヘルパー関数です。

以下のアクションオプションが含まれています

  * [`flat_start!`](@ref flat_start!)
  * [`neglect_line_charging!`](@ref neglect_line_charging!)
  * [`neglect_transformer!`](@ref neglect_transformer!)
  * [`zero_gen_setpoints!`](@ref zero_gen_setpoints!)
