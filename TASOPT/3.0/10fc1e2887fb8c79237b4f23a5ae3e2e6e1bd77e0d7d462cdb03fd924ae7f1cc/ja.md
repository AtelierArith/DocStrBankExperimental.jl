```
read_aircraft_model(datafile; 
defaultfile = joinpath(TASOPT.__TASOPTroot__, "../example/defaults/default_input.toml"))
```

指定されたTOMLファイルを読み込み、TASOPT `aircraft` モデルを記述します。"/example/defaults/default_input.toml" に提供されているデフォルトの `aircraft` 定義にフォールバックします。

!!! note "デフォルトからの逸脱"
    デフォルトの機能から大きく逸脱するモデルには、`read_input.jl` と `save_model.jl` の拡張が推奨されます。モデルに関する十分な知識が必要です。


# 例

```julia-repl
julia> read_aircraft_model("examples/defaults/default_input.toml")


┌ Info: engine_location がユーザー指定の入力ファイルに見つかりませんでした。 
│ デフォルトのTASOPT入力から engine_location を読み込みます:
│ 
│ engine_location = wing
└ 

┌ Info: pylon_weight_fraction がユーザー指定の入力ファイルに見つかりませんでした。 
│ デフォルトのTASOPT入力から pylon_weight_fraction を読み込みます:
│ 
│ pylon_weight_fraction = 0.1
└ 
名前: Example TASOPT Model;
Wpay = 210.0 kN
設計範囲  = 5.56e6 km
巡航マッハ = 0.8

```
