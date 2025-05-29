```
write_weather(
    file, w; 
    vars=setdiff(propertynames(w), ATMOSPHERE_COMPUTED),
    duration=Dates.Minute
)
```

天気データをファイルに書き込みます。

# 引数

  * `file`: 書き込むファイルのパスを表す `String`
  * `w`: `TimeStepTable{Atmosphere}`
  * `vars`: 書き込む変数のベクトル（シンボルとして）。デフォルトでは、再計算可能な変数を除いてすべての変数が書き込まれます（[`ATMOSPHERE_COMPUTED`](@ref)を参照）。`nothing` が指定された場合、すべての変数が書き込まれます。
  * `duration`: 時間ステップの持続時間をフォーマットするための単位。デフォルトでは `Dates.Minute` です。

# 例

```julia
using PlantMeteo, Dates

file = joinpath(dirname(dirname(pathof(PlantMeteo))),"test","data","meteo.csv")
w = read_weather(
    file,
    :temperature => :T,
    :relativeHumidity => (x -> x ./100) => :Rh,
    :wind => :Wind,
    :atmosphereCO2_ppm => :Cₐ,
    date_format = DateFormat("yyyy/mm/dd")
)

write_weather("meteo.csv", w)
```
