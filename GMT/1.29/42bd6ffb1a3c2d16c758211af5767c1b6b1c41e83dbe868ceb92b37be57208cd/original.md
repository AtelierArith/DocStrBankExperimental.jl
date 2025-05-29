```
sphinterpolate(cmd0::String="", arg1=nothing, kwargs...)
```

Spherical gridding in tension of data on a sphere

See full GMT (not the `GMT.jl` one) docs at [`sphinterpolate`](http://docs.generic-mapping-tools.org/latest/sphinterpolate .html)

## Parameters

  * **D** | **skipdup** :: [Type => Bool]

    Delete any duplicate points [Default assumes there are no duplicates].
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = sphinterpolate(....) form.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **Q** | **tension** :: [Type => Number | Str]     $Arg = mode[/options]$

    Specify one of four ways to calculate tension factors to preserve local shape properties or satisfy arc constraints.
  * **T** | **var_tension** :: [Type => Bool | Str]

    Use variable tension (ignored with -Q0 [constant]
  * **Z** | **scale** :: [Type => Bool | Str]

    Before interpolation, scale data by the maximum data range [no scaling].
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
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
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? sphinterpolate$
