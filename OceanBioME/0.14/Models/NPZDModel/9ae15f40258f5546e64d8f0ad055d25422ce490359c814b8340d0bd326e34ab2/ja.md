```
NutrientPhytoplanktonZooplanktonDetritus(; grid::AbstractGrid{FT},
                                           initial_photosynthetic_slope::FT = 0.1953 / day, # 1/(W/m²)/s
                                           base_maximum_growth::FT = 0.6989 / day, # 1/s
                                           nutrient_half_saturation::FT = 2.3868, # mmol N/m³
                                           base_respiration_rate::FT = 0.066 / day, # 1/s/(mmol N / m³)
                                           phyto_base_mortality_rate::FT = 0.0101 / day, # 1/s/(mmol N / m³)
                                           maximum_grazing_rate::FT = 2.1522 / day, # 1/s
                                           grazing_half_saturation::FT = 0.5573, # mmol N/m³
                                           assimulation_efficiency::FT = 0.9116, 
                                           base_excretion_rate::FT = 0.0102 / day, # 1/s/(mmol N / m³)
                                           zoo_base_mortality_rate::FT = 0.3395 / day, # 1/s/(mmol N / m³)²
                                           remineralization_rate::FT = 0.1213 / day, # 1/s

                                           surface_photosynthetically_active_radiation = default_surface_PAR,
                                           light_attenuation_model::LA =
                                               TwoBandPhotosyntheticallyActiveRadiation(; grid,
                                                                                          surface_PAR = surface_photosynthetically_active_radiation),
                                           sediment_model::S = nothing,
            
                                           sinking_speeds = (P = 0.2551/day, D = 2.7489/day),
                                           open_bottom::Bool = true,

                                           scale_negatives = false,
                                                                                  
                                           particles::P = nothing,
                                           modifiers::M = nothing)
```

栄養素-植物プランクトン-動物プランクトン-デトリタス ([NPZD](@ref NPZD)) 生物地球化学モデルを構築します。

# キーワード引数

  * `grid`: (必須) モデルを構築するための幾何学、沈降を計算するために必要
  * `initial_photosynthetic_slope`, ..., `remineralization_rate`: NPZD パラメータ値
  * `surface_photosynthetically_active_radiation`: 表面での光合成可能な放射線の関数 (または将来的には配列)、形状は `f(x, y, t)` である必要があります
  * `light_attenuation_model`: 利用可能な光の減衰を統合する光減衰モデル
  * `sediment_model`: `BiogeochemicalSediment` のスロット
  * `sinking_speed`: 沈降する任意のトレーサーのための定数沈降の名前付きタプル、フィールド (すなわち `ZFaceField(...)`) のフィールド (沈降速度は正であることが慣例ですが、フィールドは通常の下向きが負であることに従う必要があります)
  * `open_bottom`: トレーサーが領域を離れるのを防ぐために、沈降速度を底で滑らかにゼロにするべきか
  * `scale_negatives`: 負のトレーサーをスケールしますか？
  * `particles`: `BiogeochemicalParticles` のスロット
  * `modifiers`: 傾向が計算された後や状態が更新されたときに生物地球化学を修正するコンポーネントのスロット

# 例

```jldoctest
julia> using OceanBioME

julia> using Oceananigans

julia> grid = RectilinearGrid(size=(20, 30), extent=(200, 200), topology=(Bounded, Flat, Bounded));

julia> model = NutrientPhytoplanktonZooplanktonDetritus(; grid)
NutrientPhytoplanktonZooplanktonDetritus{Float64} model, with (:P, :D) sinking 
 Light attenuation: Two-band light attenuation model (Float64)
 Sediment: Nothing
 Particles: Nothing
 Modifiers: Nothing
```
