```
gmtwrite(fname::AbstractString, data; kwargs...)
```

Write a GMT object to file. The object is one of "grid" or "grd", "image" or "img", "dataset" or "table", "cmap" or "cpt" and "ps" (for postscript).

When saving grids, images and datasets we have a panoply of formats at our disposal. For the datasets case if the file name ends in .arrow, .shp, .json, .feather, .geojson, .gmt, .gpkg, .gpx, .gml or .parquet then it automatically selects $gdalwrite$ and saves the GMT dataset in that OGR vector format. The .kml is treated as a special case because there are GMT modules (e.g. `gmt2kml`) that produce KML formatted data and so we write it directly as a text file.

## Parameters

  * `binary`: Applyes only when saving a `stl` file. By default it is true. Use `binary=false` to save in ascii.
  * `id`:  [Type => Str] 

    Use an $id$ code when not not saving a grid into a standard COARDS-compliant netCDF grid. This $id$   is made up of two characters like $ef$ to save in ESRI Arc/Info ASCII Grid Interchange format (ASCII float).   See the full list of ids at http://docs.generic-mapping-tools.org/latest/grdconvert.html#format-identifier.

    (http://docs.generic-mapping-tools.org/latest/grdconvert.html#g)
  * `scale` | `offset`: [Type => Number]

    You may optionally ask to scale the data and then offset them with the specified amounts.   These modifiers are particularly practical when storing the data as integers, by first removing an offset   and then scaling down the values. The `scale` factor can also be applied when saving to stl (scales the z values).
  * `nan` | `novalue` | `invalid` | `missing`: [Type => Number]

    Lets you supply a value that represents an invalid grid entry, i.e., ‘Not-a-Number’.
  * `gdal`: [Type => Bool]

    Force the use of the GDAL library to write the grid (to be used only with grids).   (http://docs.generic-mapping-tools.org/latest/GMT_Docs.html#grid-file-format-specifications)
  * `driver`: [Type => Str]

    When saving in other than the netCDF format we must tell the GDAL library what is wished format.   That is done by specifying the driver name used by GDAL itself (e.g., netCDF, GTiFF, etc...).
  * `datatype`: [Type => Str] 		$Arg = u8|u16|i16|u32|i32|float32$

    When saving with GDAL we can specify the data type from u8|u16|i16|u32|i32|float32 where ‘i’ and ‘u’ denote   signed and unsigned integers respectively.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary output.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

Example: write the GMTgrid 'G' object into a nc file called 'lixo.grd'

```
gmtwrite("lixo.grd", G);
```
