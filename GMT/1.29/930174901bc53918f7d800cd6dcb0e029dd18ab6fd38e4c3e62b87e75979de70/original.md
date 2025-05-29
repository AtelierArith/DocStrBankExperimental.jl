```
grdblend(cmd0::String="", arg1=nothing, arg2=nothing, kwargs...)
```

Reads a listing of grid files and blend parameters, or up to 2 GTMgrid types, and creates a grid by blending the other grids using cosine-taper weights.

See full GMT (not the `GMT.jl` one) docs at [`grdblend`](http://docs.generic-mapping-tools.org/latest/grdblend.html)

## Parameters

  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.   (http://docs.generic-mapping-tools.org/latest/grdblend.html#i)
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdblend(....) form.
  * **C** | **clobber** :: [Type => Str | []]      $Arg = f|l|o|u[±]$

    Clobber mode: Instead of blending, simply pick the value of one of the grids that covers a node.
  * **N** | **nodata** :: [Type => Str | Number]

    No data. Set nodes with no input grid to this value [Default is NaN].
  * **Q** | **headless** :: [Type => Bool]

    Create plain header-less grid file (for use with external tools). Requires that the output   grid file is a native format (i.e., not netCDF). DO NOT USE WITH **G**.
  * **W** | **no_blend** :: [Type => Str | []]

    Do not blend, just output the weights used for each node [Default makes the blend].   Append $z$ to write the weight*z sum instead.
  * **Z** | **scale** :: [Type => Number]

    Scale output values by scale before writing to file.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Select grid interpolation mode by adding b for B-spline smoothing, c for bicubic interpolation,   l for bilinear interpolation, or n for nearest-neighbor value.
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
