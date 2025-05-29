```
convert_outputs(sim_outputs::Dict{String,O} where O, sink; refvectors=false, no_value=nothing)
convert_outputs(sim_outputs::TimeStepTable{T} where T, sink)
```

シミュレーションによって返された出力を別の形式に変換します。

# 詳細

最初のメソッドはマルチスケールシミュレーションの出力に対して動作し、2番目のメソッドは典型的な単一スケールシミュレーションの出力に対して動作します。sink関数は、使用される形式を決定します。例えば、`DataFrame`のようなものです。

# 引数

  * `sim_outputs` : 以前のシミュレーションの出力で、通常は`run!`によって返されます。
  * `sink`: Tables.jlインターフェースに互換性のあるsink（*例* `DataFrame`）
  * `refvectors`: `false`（デフォルト）の場合、関数はRefVector値を削除します。それ以外の場合は保持します。
  * `no_value`: `nothing`値を置き換えるための値。デフォルトは`nothing`です。通常、DataFrames内の`nothing`値を`missing`に置き換えるために使用されます。

# 例

```@example
using PlantSimEngine, MultiScaleTreeGraph, DataFrames, PlantSimEngine.Examples
```

例のモデルをインポートします（パッケージの`examples`フォルダーまたは`Examples`サブモジュールにあります）：

```jldoctest mylabel
julia> using PlantSimEngine.Examples;
```

```@example
mapping = Dict( "Plant" =>  ( MultiScaleModel(  model=ToyCAllocationModel(), mapped_variables=[ :carbon_assimilation => ["Leaf"], :carbon_demand => ["Leaf", "Internode"], :carbon_allocation => ["Leaf", "Internode"] ], ), 
        MultiScaleModel(  model=ToyPlantRmModel(), mapped_variables=[:Rm_organs => ["Leaf" => :Rm, "Internode" => :Rm],] ), ),"Internode" => ( ToyCDemandModel(optimal_biomass=10.0, development_duration=200.0), ToyMaintenanceRespirationModel(1.5, 0.06, 25.0, 0.6, 0.004), Status(TT=10.0) ), "Leaf" => ( MultiScaleModel( model=ToyAssimModel(), mapped_variables=[:soil_water_content => "Soil",], ), ToyCDemandModel(optimal_biomass=10.0, development_duration=200.0), ToyMaintenanceRespirationModel(2.1, 0.06, 25.0, 1.0, 0.025), Status(aPPFD=1300.0, TT=10.0), ), "Soil" => ( ToySoilWaterModel(), ), )
```

```@example
mtg = import_mtg_example();
```

```@example
out = run!(mtg, mapping, meteo, tracked_outputs = Dict(
    "Leaf" => (:carbon_assimilation, :carbon_demand, :soil_water_content, :carbon_allocation),
    "Internode" => (:carbon_allocation,),
    "Plant" => (:carbon_allocation,),
    "Soil" => (:soil_water_content,),
));
```

```@example
convert_outputs(out, DataFrames)
```
