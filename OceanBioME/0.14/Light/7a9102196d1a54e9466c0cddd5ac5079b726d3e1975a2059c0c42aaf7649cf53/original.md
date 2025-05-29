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
```

# Keyword Arguments

  * `grid`: grid for building the model on
  * `water_red_attenuation`, ..., `phytoplankton_chlorophyll_ratio`: parameter values
  * `surface_PAR`: function (or array in the future) for the photosynthetically available radiation at the surface,   which should be `f(x, y, t)` where `x` and `y` are the native coordinates (i.e. meters for rectilinear grids  and latitude/longitude as appropriate)
