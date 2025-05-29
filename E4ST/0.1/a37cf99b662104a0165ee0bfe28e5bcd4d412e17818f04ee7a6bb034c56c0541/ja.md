```
InterfaceLimit(;file)
```

地域間の電力の流れを各代表時間ごとに制約します。 [`summarize_table(::Val{:interface_limit})`](@ref) を参照してください。

  * [`modify_raw_data!(mod::InterfaceLimit, config, data)`](@ref)
  * [`modify_model!(mod::InterfaceLimit, config, data, model)`](@ref)

各年および/または各時間の電力の流れの最小/最大を変更するには、[`AdjustYearly`](@ref) および [`AdjustHourly`](@ref) を参照してください。
