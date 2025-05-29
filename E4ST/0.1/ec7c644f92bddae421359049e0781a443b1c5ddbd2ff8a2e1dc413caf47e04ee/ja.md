```
FuelPrice(;file, fp_scalar=1e3) <: Modification
```

FuelPriceは、地域ごとに異なる燃料の価格を指定できる[`Modification`](@ref)です。複数のステップと数量が与えられた場合、特定の地域の燃料価格は内生的に計算されます。

  * [`modify_raw_data!(mod::FuelPrice, config, data)`](@ref)
  * [`modify_setup_data!(mod::FuelPrice, config, data)`](@ref)
  * [`modify_model!(mod::FuelPrice, config, data, model)`](@ref)
  * [`modify_results!(mod::FuelPrice, config, data)`](@ref)

時間や年ごとに価格を調整するには、[`AdjustHourly`](@ref)または[`AdjustYearly`](@ref)を参照してください。

## フィールド

  * `file` - 燃料ステップのテーブルへのファイルパス。[`summarize_table(::Val{:fuel_price})`](@ref)を参照してください。
  * `fp_scalar = 1e3` - 燃料価格変数をスケールするための`Float64`。これは、いくつかの燃料ステップが非常に大きく、モデルのRHSおよび境界範囲を膨張させる可能性があるため、数値的不安定性を助けます。例えば、デフォルト値の1e3は、数量変数がMMBtuではなく千のMMBtuの単位で表されることを意味します。
