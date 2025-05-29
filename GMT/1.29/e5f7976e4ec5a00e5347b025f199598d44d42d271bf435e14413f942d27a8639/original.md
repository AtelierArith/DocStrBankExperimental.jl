```
sphdistance(cmd0::String="", arg1=nothing, kwargs...)
```

Create Voronoi distance, node, or natural nearest-neighbor grid on a sphere

See full GMT (not the `GMT.jl` one) docs at [`sphdistance`](http://docs.generic-mapping-tools.org/latest/sphdistance.html)

## Parameters

  * **C** | **save_mem** :: [Type => Bool]

    For large data sets you can save some memory (at the expense of more processing).
  * **D** | **duplicates** :: [Type => Bool]

    Delete any duplicate points [Default assumes there are no duplicates].
  * **E** | **quantity** :: [Type => Str]   $Arg = d|n|z[dist]$

    Specify the quantity that should be assigned to the grid nodes.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = sphdistance(....) form.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **L** | **dist_unit** :: [Type => Str]      $Arg = d|e|f|k|M|n|u$

    Specify the unit used for distance calculations.
  * **N** | **nodes** :: [Type => Str]      $Arg = nodes$

    Read the information pertaining to each Voronoi polygon (the unique node lon, lat and polygon area)   from a separate file.
  * **Q** | **voronoi** :: [Type => Str]     $Arg = voronoifile$

    Append the name of a file with pre-calculated Voronoi polygons.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? sphdistance$
