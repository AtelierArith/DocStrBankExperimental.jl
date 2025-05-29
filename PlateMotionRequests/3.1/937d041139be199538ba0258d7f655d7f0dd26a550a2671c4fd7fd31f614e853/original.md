```
platemotion(lats, lons, heights; kwargs...)
platemotion(lats, lons; kwargs...)
```

Request plate motion data from the [UNAVCO Plate Motion Calculator][1]. Headers and metadata are stripped from the output, which is parsed into a [`Table`][2]. Accepts either separate vectors for latitude, longitude and optionally height.

See also: [`write_platemotion`](@ref).

!!! note
    Site names are not supported. Only 'ansii', 'ansii_xyz' and 'psvelo' formats are supported. Not all optional argument permutations are permitted, see the website linked above for further details.


Optional arguments:

  * `model`: The plate motion model to use for calculations, or GSRM v2.1 by default.
  * `plate`: The tectonic plate of attributed motion, or automatic plate selection by default.
  * `reference`: The fixed reference plate, or NNR (No Net Rotation) by default.
  * `up_lat`: Custom coordinate of the Euler pole (attributed motion) in decimal degrees.
  * `up_lon`: See above.
  * `up_w`: Custom rotation rate (attributed motion) in degrees per million years.
  * `up_x`: Custom component of the Euler pole (attributed motion) in degrees per million years.
  * `up_y`: See above.
  * `up_z`: See above.
  * `ur_lat`: Custom coordinate of the Euler pole (reference velocity) in decimal degrees.
  * `ur_lon`: See above.
  * `ur_w`: Custom rotation rate of the Euler pole (reference velocity) in degrees per million years.
  * `ur_x`: Custom component of the Euler pole (reference velocity) in degrees per million years.
  * `ur_y`: See above.
  * `ur_z`: See above.
  * `format`: Output format for the data section of the response, or ASCII by default.

[1]: https://www.unavco.org/software/geodetic-utilities/plate-motion-calculator/plate-motion-calculator.html. [2]: https://typedtables.juliadata.org/latest/man/table/
