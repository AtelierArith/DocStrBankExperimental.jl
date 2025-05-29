```
MultiBandPhotosyntheticallyActiveRadiation(; grid::AbstractGrid{FT}, 
                                             bands = ((400, 500), (500, 600), (600, 700)), #nm
                                             base_bands = MOREL_λ,
                                             base_water_attenuation_coefficient = MOREL_kʷ,
                                             base_chlorophyll_exponent = MOREL_e,
                                             base_chlorophyll_attenuation_coefficient = MOREL_χ,
                                             field_names = [par_symbol(n, length(bands)) for n in 1:length(bands)],
                                             surface_PAR = default_surface_PAR)
```

Returns a `MultiBandPhotosyntheticallyActiveRadiation` attenuation model of `surface_PAR` in divided  into `bands` by `surface_PAR_division`. 

The attenuation morel*coefficients are computed from `base*water*attenuation*coefficient`,`base*chlorophyll*exponent`, and`base*chlorophyll*attenuation*coefficient`which should be  arrays of the coefficients at`base*bands` wavelengths. 

The returned `field_names` default to `PAR₁`, `PAR₂`, etc., but may be specified by the user instead.

# Keyword Arguments

  * `grid`: grid for building the model on
  * `water_red_attenuation`, ..., `phytoplankton_chlorophyll_ratio`: parameter values
  * `surface_PAR`: function (or array in the future) for the photosynthetically available radiation at the surface,   which should be `f(x, y, t)` where `x` and `y` are the native coordinates (i.e. meters for rectilinear grids  and latitude/longitude as appropriate)
