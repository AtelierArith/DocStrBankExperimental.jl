```
mbgetdata(cmd0::String=""; kwargs...)
```

Extract bathymetry, sidescan or amplitude data from datafiles.

## Parameters

  * **A** | **flagged** :: [Type => Number]	$Arg = value$

    Replace flagged beans with NaN. Use -A<val> to assign a constant value to the flagged beans.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **C** | **datatype** | **data_type** :: [Type => Number | Str | Tuple]	$Arg = 0 or "a"$

    Output SideScan, or amplitude, instead of bathymetry. This case ignores **A**
  * **D** | **scaling** :: [Type => Str | Tuple]	$Arg = <mode>/<ampscale>/<ampmin>/<ampmax>$

    Sets scaling of beam amplitude or sidescan pixel values which can be applied before plotting.
  * **F** | **format** :: [Type => Int]

    Sets the format for the input swath sonar data using MBIO integer format identifiers.
  * **S** | **speed** :: [Type => Number]

    Sets the parameters controlng simulated illumination of bathymetry.
  * **T** | **timegap** :: [Type => number]

    Sets the maximum time gap in minutes between adjacent pings before being considered a gap.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Select grid interpolation mode by adding b for B-spline smoothing, c for bicubic interpolation,   l for bilinear interpolation, or n for nearest-neighbor value.
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
