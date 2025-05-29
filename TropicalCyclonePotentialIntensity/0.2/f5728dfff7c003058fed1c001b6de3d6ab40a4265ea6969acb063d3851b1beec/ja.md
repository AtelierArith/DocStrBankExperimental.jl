```
get_potential_intensity_of_tropical_cyclone(sea_surface_temp <: Real,
sea_surface_pressure <: Real, 
pressure :: Array{<: Real}, 
temperature :: Array{<: Real},
 mixing_ratio :: Array{<: Real}; 
ckovercd = 0.9, reversible_ascent=1, dissipative_heating = true)
```

エマニュエルの潜在強度理論を使用して、熱帯サイクロンの中心での最小圧力と最大風速を計算します。
