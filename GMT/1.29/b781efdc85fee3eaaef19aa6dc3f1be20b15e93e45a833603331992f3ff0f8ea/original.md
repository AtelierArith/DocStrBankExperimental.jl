```
gmtread(fname::String; kwargs...)
```

Read GMT object from file. The object is one of "grid" or "grd", "image" or "img", "data" or "table", "cmap" or "cpt" and "ps" (for postscript), and OGR formats (shp, kml, json). Use a type specificatin to force a certain reading path (e.g. `grd=true` to read grids) or take the chance of letting the data type be guessed via the file extension. Known extensions are:

  * Grids:      .grd .jp2 .nc
  * Images:     .jpg .jp2 .png, .tif, .tiff, .bmp, .webp
  * Datasets:   .dat .txt .csv .isf
  * Datasets:   .arrow .arrows .shp .kml .kmz .json .gmt .feather .fgb .gpkg .geojson .gpx .gml .ipc .parquet .sqlite
  * CPT:        .cpt
  * PostScript: .ps, .eps

## Parameters

Specify data type (with *type*=true, e.g. `img=true`).  Choose among:

  * `grd` | `grid`: Load a grid.
  * `img` | `image`: Load an image.
  * `cpt` | `cmap`: Load a GMT color palette.
  * `data` | `dataset` | `table`: Load a dataset (a table of numbers).
  * `ogr`: Load a dataset via GDAL OGR (a table of numbers). Many things can happen here.
  * `ps`: Load a PostScript file
  * `gdal`: Force reading the file via GDAL. Should only be used to read grids.
  * `varname`: When netCDF files have more than one 2D (or higher) variables use *varname* to pick the wished variable. e.g. $varname=:slp$ to read the variable named $slp$. This option defaults data type to `grid`. This option can be used both with and without the `gdal` option. Former case uses GMT lib to read the cube and outputs and 3D array in column major order, later case (the one with `gdal`) uses GDAL to read the cube and outputs and 3D array in row major order. Remember that the $layout$ member of the GMTgrid type informs about memory layout.
  * `inrows`: Select specific data rows to be read. Valid args include ranges or a string with an hard core GMT -q option.
  * `nodata`: When reading table data via GMT (but not GDAL), this option allows user-coded missing data values to be translated to NaN values. By default examine all input columns after the first two. Use the +c modifier to override the starting column used for the examinations. e.g. `nodata=-99999+c1` to replace all -99999 values in second column with NaNs.
  * `stride`: When reading table data via GMT (but not GDAL), this option allows subsampling the data. Provide a number to be used as stride for the rows. A `stride=2` will read every other row.
  * `layer`| `layers` | `band` | `bands`: A string, a number or an Array. When files are multiband or nc files with 3D or 4D arrays, we access them via these keywords. `layer=4` reads the fourth layer (or band) of the file. The file can be a grid or an image. If it is a grid, layer can be a scalar (to read 3D arrays) or an array of two elements (to read a 4D array). Use `layers=:all` to read all layers.

    If file is an image, `layer` can be a 1 or a 1x3 array (to read a RGB image). Note that in this later case bands do not need to be contiguous. A `band=[1,5,2]` composes an RGB out of those bands. See more at http://docs.generic-mapping-tools.org/latest//GMT_Docs.html#modifiers-for-coards-compliant-netcdf-files) but note that we use **1 based** indexing here.

    Use $layers=:all$ to read all levels of a 3D cube netCDF file.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

Example: to read a nc called 'lixo.grd'

```
G = gmtread("lixo.grd");
```

to read a jpg image with the bands reversed

```
I = gmtread("image.jpg", band=[2,1,0]);
```
