```
rose(cmd0::String="", arg1=nothing; kwargs...)
```

Reads (length,azimuth) pairs and plot a windrose diagram (polar histograms).

See full GMT (not the `GMT.jl` one) docs at [`psrose`](http://docs.generic-mapping-tools.org/latest/rose.html)

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **A** | **sector** | **sectors** :: [Type => Str | Number]

```
Gives the sector width in degrees for sector and rose diagram.
```

  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **color** :: [Type => Str | GMTcpt]

```
Give a CPT. The mid x-value for each bar is used to look-up the bar color.
```

  * **E** | **vectors** :: [Type => Str]

```
Plot vectors showing the principal directions given in the mode_file file.
```

  * **D** | **shift** :: [Type => Bool]

```
Shift sectors so that they are centered on the bin interval (e.g., first sector is centered on 0 degrees).
```

  * **F** | **no_scale** :: [Type => Bool]

```
Do not draw the scale length bar [Default plots scale in lower right corner].
```

  * **G** | **fill** :: [Type => Str | Number]

```
Selects shade, color or pattern for filling the sectors [Default is no fill].
```

  * **I** | **inquire** :: [Type => Bool]

```
Inquire. Computes statistics needed to specify a useful -R. No plot is generated.
```

  * **L** | **labels** :: [Type => Str | Number]

```
Specify labels for the 0, 90, 180, and 270 degree marks.
```

  * **M** | **vector_params** :: [Type => Str]

```
Used with -C to modify vector parameters.
```

  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **alpha** :: [Type => Str | []]

```
Sets the confidence level used to determine if the mean resultant is significant.
```

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **norm** | **normalize** :: [Type => Bool]

```
Specifies radius of plotted circle (append a unit from c|i|p).
```

  * **T** | **orientation** :: [Type => Bool]

```
Specifies that the input data are orientation data (i.e., have a 180 degree ambiguity)
instead of true 0-360 degree directions [Default].
```

  * **W** | **pen** :: [Type => Str | Tuple]

```
Set pen attributes for sector outline or rose plot. [Default is no outline].
```

  * **Z** | **scale** :: [Type => Str]

```
Multiply the data radii by scale.
```

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

To see the full documentation type: $@? rose$
