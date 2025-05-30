```
TwoBandPhotosyntheticallyActiveRadiation(; grid::AbstractGrid{FT}, 
                                           water_red_attenuation::FT = 0.225, # 1/m
                                           water_blue_attenuation::FT = 0.0232, # 1/m
                                           chlorophyll_red_attenuation::FT = 0.037, # 1/(m * (mgChl/m³) ^ eʳ)
                                           chlorophyll_blue_attenuation::FT = 0.074, # 1/(m * (mgChl/m³) ^ eᵇ)
                                           chlorophyll_red_exponent::FT = 0.629,
                                           chlorophyll_blue_exponent::FT = 0.674,
                                           pigment_ratio::FT = 0.7,
                                           phytoplankton_chlorophyll_ratio::FT = 1.31,
                                           surface_PAR::SPAR = default_surface_PAR)

# キーワード引数

  * `grid`: モデルを構築するためのグリッド
  * `water_red_attenuation`, ..., `phytoplankton_chlorophyll_ratio`: パラメータ値
  * `surface_PAR`: 表面での光合成可能放射線のための関数（または将来的には配列）、これは `f(x, y, t)` であるべきで、`x` と `y` はネイティブ座標（すなわち、直線グリッドの場合はメートル、適切な場合は緯度/経度）
```
