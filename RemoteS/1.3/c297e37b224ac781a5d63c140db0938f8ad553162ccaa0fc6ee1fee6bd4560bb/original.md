```
VARI = vari(red, green, blue; kw...)
```

or (here fname is a .png or .jpg file name)

```
VARI = vari(fname::String; kw...)
```

or

```
VARI = vari(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

Visible Atmospherically Resistant Index. Gitelson, A.A., Kaufman, Y.J., Stark, R., Rundquist, D., 2002

VARI = (green - red) / (green + red - blue)

  * The first form accepts inputs as matrices, or file names of the data bands.
  * The last form is more versatile but also more complex to describe.

      * `cube`: Is the file name of a 'cube', a multi-layered file normally created with the [`cutcube`](@ref) function.  If this file was created with band descriptions one can use the `bands` or the `bandnames` options.
      * `bands`: *cubes* created with [`cutcube`](@ref) assign descriptions starting with "Band1 ..." an so on the other bands. So when `bands` is used we search for bands named "Band'band[k]'", where band[k] loops over all elements of the `bands` vector. WARNING: the elements order in the vector must be sorted in increasing wavelength numbers, *i.e.* like the example for the first form.
      * `layers`: Use this option when you are certain of the bands order in the cube or the it doesn't have a bands description. The selection will be made with cube[:,:,layer[1]], etc... WARNING: same warn as above.
      * `bandnames`: When we know the common designation of a band, for example "Green", or any part of a band description, for example "NIR", we can use that info to create a `bandnames` string vector that will be matched against the cube's bands descriptions.

### Kwargs

  * `threshold`: When a threshold is provided we return a GMTgrid where `vals[ij] < threshold = NaN`
  * `classes`: is a vector with up to 3 elements (class separators) and we return a  UInt8 GMTimage with the indices categorized into vals[ij] > classes[1] = 1; vals[ij] > classes[2] = 2; vals[ij] > classes[3] = 3 and 0 otherwise.
  * `mask`: Used together with `threshold` outputs a UInt8 GMTimage mask with `vals[ij] >= threshold = 255` and 0 otherwise  If `mask=-1` (or any other negative number) we compute instead a mask where `vals[ij] < threshold = 255` and 0 otherwise
  * `save`: Use `save="file_name.ext"` to save the result in a disk file. File format is picked from file extension.
  * `order` | `bands_order` | `rgb`: For the $GLI$, $TGI$ and $VARI$ (RGB) indices, we allow to reorder the bands and change the expected RGB order. Pass in a string, or symbol, with the color order. For example, `order=:rbg`

```
will swap the green and blue components making the result index identify the _reds_ instead of the _greens_.
Not good for vegetation indices, but potentially useful for other purposes.
```

If none of `bands`, `layers` or `bandnames` is provided, we use the default band names shown in the first form.

See also https://www.indexdatabase.de/ for a list of indices and the appropriate band names per sensor.

Returns either a Float32 GMTgrid or a UInt8 GMTimage if the `mask` or `classes` options are used.
