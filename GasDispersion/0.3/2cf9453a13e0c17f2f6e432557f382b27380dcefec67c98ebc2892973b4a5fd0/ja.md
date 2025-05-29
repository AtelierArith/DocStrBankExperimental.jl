```
Substance{N,VAP,D_G,D_L,F,H,CP_G,CP_L}(;kwargs...)
```

物質の物理的および熱的特性のためのシンプルなコンテナです。

`vapor_pressure`、`latent_heat`、`gas_heat_capacity`、および `liquid_heat_capacity` は、温度（ケルビン）または定数の関数である可能性があります。

`gas_density` と `liquid_density` は、温度（ケルビン）および圧力（パスカル）の関数であるか、定数である可能性があります。

# 引数

  * `name<:Union{AbstractString,Symbol}`: 物質の名前
  * `molar_weight::Number`: モル重量、kg/mol
  * `vapor_pressure<:Union{Number,Function,Nothing}=nothing`: 蒸気圧、Pa。`nothing` の場合、クラウジウス-クラペイロンの方程式を使用して蒸気圧曲線を導出します。
  * `gas_density<:Union{Number,Function,Nothing}=nothing`: ガス密度、kg/m³。`nothing` の場合、理想気体の法則が使用されます。
  * `liquid_density<:Union{Number,Function}`: 液体密度、kg/m³。
  * `reference_temp::Number=288.15`: 指定された特性の基準温度、K。
  * `reference_pressure::Number=101325`: 指定された特性の基準圧力、Pa。
  * `k::Number=1.4`: 等エントロピー膨張係数、cp/cv、無次元。
  * `boiling_temp<:Union{Number,Function}::Number`: 正常沸点、K。
  * `latent_heat<:Union{Number,Function}`: 蒸発の潜熱、J/kg。
  * `gas_heat_capacity<:Union{Number,Function}`: ガスの比熱、J/kg/K。
  * `liquid_heat_capacity<:Union{Number,Function}`: 液体の比熱、J/kg/K。
