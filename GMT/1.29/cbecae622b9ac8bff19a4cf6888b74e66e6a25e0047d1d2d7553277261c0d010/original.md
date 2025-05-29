```
mask(cmd0::String="", arg1=nothing; kwargs...)
```

Clip or mask map areas with no data table coverage

See full GMT (not the `GMT.jl` one) docs at [`psmask`](http://docs.generic-mapping-tools.org/latest/mask.html)

## Parameters

  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **endclip** | **end*clip*path** :: [Type => Bool]

    Mark end of existing clip path. No input file is needed.
  * **D** | **dump** :: [Type => Str]

    Dump the (x,y) coordinates of each clipping polygon to one or more output files   (or stdout if template is not given).
  * **F** | **oriented** :: [Type => Str | []]

    Force clip contours (polygons) to be oriented so that data points are to the left (-Fl [Default]) or right (-Fr)
  * **G** | **fill** :: [Type => Number | Str]

    Set fill shade, color or pattern for positive and/or negative masks [Default is no fill].
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **nodegrid** :: [Type => Str]

    Save the internal grid with ones (data constraint) and zeros (no data) to the named nodegrid.
  * **N** | **invert** | **inverse** :: [Type => Bool]

    Invert the sense of the test, i.e., clip regions where there is data coverage.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **cut** | **cut_number** :: [Type => Number | Str]

    Do not dump polygons with less than cut number of points [Dumps all polygons].
  * **S** | **search_radius** :: [Type => Number | Str]

    Sets radius of influence. Grid nodes within radius of a data point are considered reliable.
  * **T** | **tiles** :: [Type => Bool]

    Plot tiles instead of clip polygons. Use -G to set tile color or pattern. Cannot be used with -D.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    Selects perspective view and sets the azimuth and elevation of the viewpoint [180/90].
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? mask$
