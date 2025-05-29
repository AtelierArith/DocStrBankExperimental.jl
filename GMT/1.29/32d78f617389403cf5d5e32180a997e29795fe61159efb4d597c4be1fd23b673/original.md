```
grdinterpolate(cmd0="", arg1=nothing, arg2=nothing; kwargs...)
```

Interpolate a 3-D cube, 2-D grids or 1-D series from a 3-D data cube or stack of 2-D grids.

See full GMT (not the `GMT.jl` one) docs at [`grdinterpolate`](http://docs.generic-mapping-tools.org/latest//grdinterpolate.html)

## Parameters

  * **D** | **meta** | **metadata** :: [Type => Str | NamedTuple]  

    Give one or more combinations for values xname, yname, zname (3rd dimension in cube), and dname   (data value name) and give the names of those variables and in square bracket their units
  * **E** | **crossection** :: [Type => Str | GMTdtaset | NamedTuple]

    Specify a crossectinonal profile via a file or from specified line coordinates and modifiers. If a file,   it must contain a single segment with either lon lat or lon lat dist records. These must be equidistant.
  * **F** | **interp_type** | **interpolator** :: [Type => Str]   $Arg = l|a|c|n[+1|+2]$

    Choose from l (Linear), a (Akima spline), c (natural cubic spline), and n (no interpolation:   nearest point) [Default is Akima].
  * **G** | **outfile** | **outgrid** :: [Type => Str]

    Output file name. If `range` only selects a single layer then the data cube collapses to a regular 2-D grid file
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **pt** | **track** :: [Type => Str | Tuple | Dataset]	`Arg = x/y|pointfile[+hheader]`

    Rather than compute gridded output, create tile/spatial series through the stacked grids at the given point (x/y)   or the list of points in pointfile.
  * **T** | **range** :: [Type => Str]			`Arg = [min/max/]inc[+i|n] |-Tfile|list`

    Make evenly spaced time-steps from min to max by inc [Default uses input times].
  * **Z** | **levels** :: [Type => range]			`Arg = [levels]`

    The `levels` may be specified the same way as in `range`. If not given then we default to an integer   levels array starting at 0.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary output.
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
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Select grid interpolation mode by adding b for B-spline smoothing, c for bicubic interpolation,   l for bilinear interpolation, or n for nearest-neighbor value.
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.
  * **q** | **inrow** | **inrows** :: [Type => Str]       $Arg = [i|o][~]rows[+ccol][+a|f|s]$

    Select specific data rows to be read (-qi [Default]) or written (-qo) [all].
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    Suppress output for records whose z-value equals NaN.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

When using two numeric inputs and no `outfile` option, the order of the x,y and grid is not important. That is, both of this will work: $D = grdinterpolate([0 0], G);$  or  $D = grdinterpolate(G, [0 0]);$

When using the `pt` or `crossection` options the default is to NOT ouput the redundant horizontal x,y coordinates (contrary to the GMT default). If you want to have them, use option `colinfo`, *e.g.* `colinfo="0-3"`, or use `allcols=true`.

To see the full documentation type: $@? grdinterpolate$
