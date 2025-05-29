```
contour(cmd0::String="", arg1=nothing; kwargs...)
```

Reads a table data and produces a raw contour plot by triangulation.

See full GMT (not the `GMT.jl` one) docs at [`contour`](http://docs.generic-mapping-tools.org/latest/contour.html)

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **A** | **annot** | **annotation** :: [Type => Str | Number]       $Arg = [-|[+]annot_int][labelinfo]$

    *annot_int* is annotation interval in data units; it is ignored if contour levels are given in a file.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **cont** | **contour** | **contours** | **levels** :: [Type => Str | Number | GMTcpt]  $Arg = [+]cont_int$

    Contours to be drawn may be specified in one of three possible ways.
  * **D** | **dump** :: [Type => Str]

    Dump contours as data line segments; no plotting takes place.
  * **E** | **index** :: [Type => Str | Mx3 array]

    Give name of file with network information. Each record must contain triplets of node   numbers for a triangle.
  * **G** | **labels** :: [Type => Str]

    Controls the placement of labels along the quoted lines.
  * **I** | **fill** | **colorize** :: [Type => Bool]

    Color the triangles using the color scale provided via **C**.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **mesh** :: [Type => Str | Number]

    Draw the underlying triangular mesh using the specified pen attributes (if not provided, use default pen)
  * **N** | **no_clip** :: [Type => Bool]

    Do NOT clip contours or image at the boundaries [Default will clip to fit inside region].
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **cut** :: [Type => Str | Number]         $Arg = [cut[unit]][+z]]$

    Do not draw contours with less than cut number of points.
  * **S** | **skip** :: [Type => Str | []]            $Arg = [p|t]$

    Skip all input xyz points that fall outside the region.
  * **T** | **ticks** :: [Type => Str]                 $Arg = [+|-][+a][+dgap[/length]][+l[labels]]$

    Draw tick marks pointing in the downward direction every *gap* along the innermost closed contours.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **pen** :: [Type => Str | Number]

    Sets the attributes for the particular line.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **Z** | **scale** :: [Type => Str]

    Use to subtract shift from the data and multiply the results by factor before contouring starts.
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary output.
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    Examine all output columns and if any item equals NAN substitute it with   the chosen missing data value.
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
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? contour$
