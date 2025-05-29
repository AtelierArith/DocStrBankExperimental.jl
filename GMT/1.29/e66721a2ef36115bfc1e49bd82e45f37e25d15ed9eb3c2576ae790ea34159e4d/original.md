```
grdmask(cmd0::String="", arg1=nothing, kwargs...)
```

1. It reads one or more pathfiles that each define a closed polygon.
2. The pathfiles simply represent data point locations and the mask is set to the inside or outside value depending on whether a node is within a maximum distance from the nearest data point.

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **A** | **steps** :: [Type => Str | Number]		$Arg = m|p|x|y$

    If the input data are geographic then the sides in the polygons will be approximated by great circle arcs.   When using this option sides will be regarded as straight lines.
  * **C** | **clobber** :: [Type => Str]		$Arg = f|l|o|u$

    Clobber mode: Selects the polygon whose z-value will determine the grid nodes.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdmask(....) form.
  * **N** | **out*edge*in** :: [Type => Str | List]    $Arg = [z|Z|p|P]values$

    Sets the out/edge/in that will be assigned to nodes that are outside the polygons, on the edge, or inside.   Values can be any number, including the textstring NaN [Default is 0/0/1].
  * **S** | **search_radius** :: [Type => Str | List]    $Arg = search_radius[unit] |xlim/ylim$

    Set nodes to inside, on edge, or outside depending on their distance to the nearest data point.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    Examine the spacing between consecutive data points in order to impose breaks in the line.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **j** | **spherical_dist** | **spherical** :: [Type => Str]     $Arg = e|f|g$

    Determine how spherical distances are calculated in modules that support this.
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Select grid interpolation mode by adding b for B-spline smoothing, c for bicubic interpolation,   l for bilinear interpolation, or n for nearest-neighbor value.
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    Limit the number of cores to be used in any OpenMP-enabled multi-threaded algorithms.   (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? grdmask$
