```
grdcut(cmd0::String="", arg1=[], kwargs...)
```

Produce a new outgrid which is a subregion of ingrid. The subregion is specified with $limits$ (the -R); the specified range must not exceed the range of ingrid (but see $extend$).

## Parameters

  * **E** | **rowlice** | **colslice** :: [Type => Number]

    Extract a vertical slice going along the x-column coord or along the y-row coord.
  * **F** | **clip** | **cutline** :: [Type => Str | GMTdaset | Mx2 array | NamedTuple]	`Arg = array|fname[+c] | (polygon=Array|Str, crop2cutline=Bool, invert=Bool)`

    Specify a closed polygon (either a file or a dataset). All grid nodes outside the   polygon will be set to NaN.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdcut(....) form.
  * **img** | **usegdal** | **gdal** :: [Type => Any]

    Force the cut operation to be done by GDAL. Works for images where GMT fails or even crash.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **N** | **extend** :: [Type => Str or []]

    Allow grid to be extended if new region exceeds existing boundaries. Append nodata value   to initialize nodes outside current region [Default is NaN].
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **circ_subregion** :: [Type => Str]    $Arg = [n]lon/lat/radius[unit]$

    Specify an origin and radius; append a distance unit and we determine the corresponding   rectangular region so that all grid nodes on or inside the circle are contained in the subset.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **Z** | **range** :: [Type => Str]       $Arg = [n|N |r][min/max]$

    Determine a new rectangular region so that all nodes outside this region are also outside   the given z-range.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

To see the full documentation type: $@? grdcut$
