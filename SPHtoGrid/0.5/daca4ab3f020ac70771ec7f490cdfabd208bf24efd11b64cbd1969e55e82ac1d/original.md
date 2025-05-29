```
convert_Pnu_map_to_mJy_beam(map::Matrix{<:Real}, 
                            d_pixel::Real,
                            beam::Vector{Union{Real, Unitful.AbstractQuantity}}, 
                            c::Cosmology.AbstractCosmology, 
                            z::Real)
```

Converts a map from units [W / Hz] to [mJy / beam].

## Parameters:

  * `map`: original map in [W / Hz].
  * `d_pixel`: size of a pixel in $kpc$.
  * `beam`: dimensions of the beam in $arcmin$.
  * `c`: Cosmology used for conversion.
  * `z`: Redshift of the image.
