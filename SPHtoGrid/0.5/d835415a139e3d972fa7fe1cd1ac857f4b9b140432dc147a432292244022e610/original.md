```
convert_Pnu_map_to_mJy_beam(map::Matrix{<:Real}, 
                            d_pixel::Real,
                            beam::Union{Real, Unitful.AbstractQuantity}, 
                            c::Cosmology.AbstractCosmology, 
                            z::Real)
```

Converts a map from units [W / Hz] to [mJy / beam] for a circular beam.

## Parameters:

  * `map`: original map in [W / Hz].
  * `d_pixel`: size of a pixel in $kpc$.
  * `beam`: radius of the beam in $arcmin$.
  * `c`: Cosmology used for conversion.
  * `z`: Redshift of the image.
