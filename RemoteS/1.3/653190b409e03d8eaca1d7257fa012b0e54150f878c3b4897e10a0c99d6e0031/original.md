```
cutcube(names=String[], bands=Int[], template="", region=nothing, extension=".TIF", description=String[], mtl="", sentinel2=0, save="")
```

Cut a 3D cube out of a Landsat/Sentinel scene within a subregion `region` and a selection of bands.

  * `names`: (optional) A vector with the individual bands full file name
  * `bands`: When `names` is not provided give a vector of integers corresponding to the choosen bands.          This works well for Landsat and most of Sentinel bands. However, in later case, there are also          bands that contain characters, for example band 8A. In this case `bands` should be a vector of          strings including the extension. *e.g.* ["02.jp2", "8A.jp2"]
  * `template`: Goes together with the `bands` option. They are both composed a template * band[n] to recreate          the full file name of each band.
  * `region` Is the region to extract and must contain the extracting region limits as [W, E, S, N] or a          GMT style -R string (without the leading "-R").
  * `extension`: In case the `bands` is numeric but file extensions are not "*.TIF" (case insensitive),          use the extension passed by this option.
  * `description`: A vector of strings (as many as bands) with a description for each band. If not provided and          the file is recognized as a Landasat 8, band description is added automatically, otherwise          we build one with the bands file names. This info will saved if data is written to a file.
  * `mtl`:   If reading from Landsat and the MTL file is not automatically found (you get an error) use this          option to pass the full name of the MTL file.
  * `sentinel2`: ESA is just unconsistent and names change with time and band numbers can have character (e.g. 8A)          hence we need help to recognize Sentinel files so the known description can be assigned.          Use `sentinel=10`, or `=20` or `=60` to indicate Sentinel files at those resolutions.
  * `save`:  The file name where to save the output. If not provided, a GMTimage is returned.

Return: `nothing` if the result is written in file or a GMTimage otherwise.

## Examples

```julia
# Cut a Landsat 8 scene for a small region (in UTM) and return a GMTimage with 3 bands in UInt16.
temp = "C:\SIG_AnaliseDadosSatelite\SIG_ADS\DadosEx2\LC82040332015145LGN00\LC82040332015145LGN00_B";
cube = cutcube(bands=[2,3,4], template=temp, region=[479670,492720,4282230,4294500])

# The same example as above but save the data in a GeoTIFF disk file and use a string for `region`
cutcube(bands=[2,3,4], template=temp, region="479670/492720/4282230/4294500", save="landsat_cube.tif")
```
