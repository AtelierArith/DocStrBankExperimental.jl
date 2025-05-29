```
grdproject(cmd0::String="", arg1=nothing, kwargs...)
```

Project a geographical gridded data set onto a rectangular grid or do the inverse projection.

See full GMT (not the `GMT.jl` one) docs at [`grdproject`](http://docs.generic-mapping-tools.org/latest/grdproject.html)

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **C** | **center** :: [Type => Str | []]      $Arg = [dx/dy]$

    Let projected coordinates be relative to projection center [Default is relative to lower left corner].
  * **D** | **inc** :: [Type => Str | number]     $Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]$

    Set the grid spacing for the new grid. Append m for arc minute, s for arc second.
  * **E** | **dpi** :: [Type => Number]

    Set the resolution for the new grid in dots per inch.
  * **F** | **one2one** :: [Type => Str]           $Arg = [c|i|p|e|f|k|M|n|u]$

    Force 1:1 scaling, i.e., output (or input, see -I) data are in actual projected meters [e].
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdproject(....) form.
  * **I** | **inverse** :: [Type => Bool]

    Do the Inverse transformation, from rectangular to geographical.
  * **M** | **projected_unit** :: [Type => Str]    $Arg = c|i|p$

    Append c, i, or p to indicate that cm, inch, or point should be the projected measure unit.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Select grid interpolation mode by adding b for B-spline smoothing, c for bicubic interpolation,   l for bilinear interpolation, or n for nearest-neighbor value.
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].

To see the full documentation type: $@? grdproject$
