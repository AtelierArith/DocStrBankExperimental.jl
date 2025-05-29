```
Irgb = truecolor(bndR, bndG, bndB)
```

Take three Landsat8/Sentinel2 UINT16 GMTimages or the file names of those bands and compose an RGB true color image applying automatic histogram stretching.

Return an UInt8 RGB GMTimage

```
Irgb = truecolor(cube::GMTImage, bands::Vector{Int})
```

Make an RGB composition of the 3 bands passed in the vector 'bands' from the layers in the multi-layered GMTimage `cube`

Return an auto-stretched UInt8 RGB GMTimage

```
Irgb = truecolor(cube::String, [bands::Vector{Int}], [bandnames::Vector{String}], [raw=false])
```

Make an RGB composition of 3 bands from the `cube` file holding a UInt16 multi-layered array (often created with `cutcube`) The band selection can be made with `bands` vector, case in which we will search for bands named "Band[k]" or where the bands description contain the contents of `bandnames`. If none of `bands` or `bandnames` is used we search for a made up `bandnames=["red", "green", "blue"]`.

Return an auto-stretched UInt8 RGB GMTimage OR a GMTimage{UInt16,3} if the `raw` option is set to `true`.

```
Irgb = truecolor(cube::GMTgrid, [bands|layers::Vector{Int}], [bandnames::Vector{String}], [type=UInt8])
```

Make an RGB composition of 3 bands from the `cube` file holding a Float32 multi-layered array. The band selection can be made with `bands` vector, case in which we will search for bands named "Band[k]" or where the bands description contain the contents of `bandnames`. If none of `bands` or `bandnames` is used we search for a made up `bandnames=["red", "green", "blue"]`.

By default we scale the bands to 0-255. Use `type=UInt16` to scale the bands to 0-65535`. Note that this will matter only for the guessing of the good limits to perform the histogram stretching.

### Example:

Make an RGB composite from data in the cube file "LC08__cube.tiff"

```julia
I = truecolor("LC08__cube.tiff");
```
