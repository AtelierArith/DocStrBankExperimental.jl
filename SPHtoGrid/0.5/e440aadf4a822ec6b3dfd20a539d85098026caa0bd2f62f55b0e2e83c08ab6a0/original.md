```
convert_Pnu_map_to_mJy_beam(map::Matrix{<:Real}, 
                            d_pixel::Real,
                            beam::Union{T, Vector{T}}, 
                            h::AbstractGadgetHeader) where T::Union{Real, Unitful.AbstractQuantity}
```

Converts a map from units [W / Hz] to [mJy / beam] by using a Gadget header.

## Parameters:

  * `map`: original map in [W / Hz].
  * `d_pixel`: size of a pixel in $kpc$.
  * `beam`: radius/dimensions of the beam in $arcmin$.
  * `h`: Gadget header of simulation
