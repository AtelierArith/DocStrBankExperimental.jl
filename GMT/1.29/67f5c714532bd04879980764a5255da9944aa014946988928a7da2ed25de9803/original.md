```
grdfilter(cmd0::String="", arg1=nothing, kwargs...)
```

Filter a grid file in the time domain using one of the selected convolution or non-convolution  isotropic or rectangular filters and compute distances using Cartesian or Spherical geometries.

See full GMT (not the `GMT.jl` one) docs at [`grdfilter`](http://docs.generic-mapping-tools.org/latest/grdfilter.html)

## Parameters

  * **F** | **filter** :: [Type => Str]

    Sets the filter type.
  * **D** | **distflag** | **distance** :: [Type => Number]

    Distance flag tells how grid (x,y) relates to filter width.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdfilter(....) form.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **N** | **nans** :: [Type => Str]

    Determine how NaN-values in the input grid affects the filtered output. Values are i|p|r
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **T** | **toggle** :: [Type => Bool]

    Toggle the node registration for the output grid so as to become the opposite of the input grid
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

To see the full documentation type: $@? grdfilter$
