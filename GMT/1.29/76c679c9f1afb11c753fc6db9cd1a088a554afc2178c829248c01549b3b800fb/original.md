```
grdcontour(cmd0::String="", arg1=nothing; kwargs...)
```

Read a 2-D grid file or a GMTgrid type and produces a contour map by tracing each contour through the grid.

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **A** | **annot** | **annotation** :: [Type => Str or Number]       $Arg = [-|[+]annot_int][labelinfo]$

    *annot_int* is annotation interval in data units; it is ignored if contour levels are given in a file.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **cont** | **contour** | **contours** | **levels** :: [Type => Str | Number | GMTcpt]  $Arg = [+]cont_int$

    Contours to be drawn may be specified in one of three possible ways.
  * **D** | **dump** :: [Type => Str]

    Dump contours as data line segments; no plotting takes place.
  * **F** | **force** :: [Type => Str | []]

    Force dumped contours to be oriented so that higher z-values are to the left (-Fl [Default]) or right.
  * **G** | **labels** :: [Type => Str]

    Controls the placement of labels along the quoted lines.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **range** :: [Type => Str]

    Limit range: Do not draw contours for data values below low or above high.
  * **N** | **fill** | **colorize** :: [Type => Bool]

    Fill the area between contours using the discrete color table given by cpt.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **cut** :: [Type => Str | Number]

    Do not draw contours with less than cut number of points.
  * **S** | **smooth** :: [Type => Number]

    Used to resample the contour lines at roughly every (gridbox_size/smoothfactor) interval.
  * **T** | **ticks** :: [Type => Str]

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
  * **Z** | **muladd** | **scale** :: [Type => Str]

    Use to subtract shift from the data and multiply the results by factor before contouring starts.
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary output.
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    Examine all output columns and if any item equals NAN substitute it with   the chosen missing data value.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    Selects perspective view and sets the azimuth and elevation of the viewpoint [180/90].
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? grdcontour$
