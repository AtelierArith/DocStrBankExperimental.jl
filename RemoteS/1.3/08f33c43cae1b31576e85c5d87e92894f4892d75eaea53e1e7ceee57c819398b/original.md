```
R = dn2temperature(fname::String; band::Int=0, mtl::String="", save::String)
```

Computes the brigthness temperature of Landasat8 termal band (10 or 11)

  * `fname`: The name of either a $LANDSAT_PRODUCT_ID$ geotiff band, or the name of a cube file created with the `cutcube` function. In the first case, if the companion $...MTL.txt$ file is not in the same directory as `fname` one can still pass it via the `mtl=path-to-MTL-file` option. In the second case it is mandatory to use one of the following two options.
  * `band`: *cubes* created with [`cutcube`](@ref) assign descriptions starting with "Band 1 ..." an so on the other bands. So when `band` is used we search for the band named "Band N", where N = `band`.
  * `bandname`: When we know the common designation of a band, for example "Green", or any part of a band description, for example "NIR", we can use that info to create a `bandname` string that will be matched against the cube's bands descriptions. We can use the `reportbands` function to see the bands description.
  * `save`:  The file name where to save the output. If not provided, a GMTgrid is returned.

Returns a Float32 GMTgrid

# Example:

Compute the brightness temperature of Band 10 stored in a `cube`

```
T = dn2temperature(cube, band=10)
```
