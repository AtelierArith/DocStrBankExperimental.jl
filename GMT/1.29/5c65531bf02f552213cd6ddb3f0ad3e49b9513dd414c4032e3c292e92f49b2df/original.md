```
wiggle(cmd0::String="", arg1=nothing; kwargs...)
```

Reads (length,azimuth) pairs from file and plot a windwiggle diagram.

See full GMT (not the `GMT.jl` one) docs at [`pswiggle`](http://docs.generic-mapping-tools.org/latest/wiggle.html)

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **Z** | **ampscale** | **amp_scale** :: [Type => Number | Str]

    Gives anomaly scale in data-units/distance-unit.
  * **A** | **azimuth** :: [Type => Str | number]

    Sets the preferred positive azimuth. Positive wiggles will “gravitate” towards that direction.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **center** :: [Type => Number]

    Subtract center from the data set before plotting [0].
  * **D** | **scale_bar** :: [Type => Str]

    Defines the reference point on the map for the vertical scale bar using one of four coordinate systems.
  * **F** | **box** :: [Type => Str]

    Without further options, draws a rectangular border around the vertical scale bar.
  * **G** | **fill** :: [Type => Number | Str]

    Set fill shade, color or pattern for positive and/or negative wiggles [Default is no fill].
  * **I** | **fixed_azim** :: [Type => Number]

    Set a fixed azimuth projection for wiggles [Default uses track azimuth, but see -A].
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **T** | **track** :: [Type => Number or Str | Tuple | []]

    Draw track [Default is no track]. Append pen attributes to use [Defaults: width = 0.25p, color =   black, style = solid].
  * **W** | **pen** :: [Type => Number | Str | tuple | []]

    Specify outline pen attributes [Default is no outline].
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
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? pswiggle$
