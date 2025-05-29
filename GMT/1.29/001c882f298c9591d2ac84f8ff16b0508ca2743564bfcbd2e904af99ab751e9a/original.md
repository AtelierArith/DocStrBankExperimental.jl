```
contourf(cmd0::String="", arg1=nothing; kwargs...)
```

Performs Delaunay triangulation on x,y[,z] data, i.e., it find how the points should be connected to give the most equilateral triangulation possible. 

See full GMT (not the `GMT.jl` one) docs at [`triangulate`](http://docs.generic-mapping-tools.org/latest/triangulate.html)

## Parameters

  * **A** | **annot** :: [Type => Str | Number]       $Arg = [-|[+]annot_int][labelinfo]$

    *annot_int* is annotation interval in data units; it is ignored if contour levels are given in a file.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **cont** | **contour** | **contours** | **levels** :: [Type => Str | Number | GMTcpt]  $Arg = [+]cont_int$

    Contours to be drawn may be specified in one of three possible ways.
  * **E** | **index** :: [Type => Str | Mx3 array]

    Give name of file with network information. Each record must contain triplets of node   numbers for a triangle.
  * **G** | **labels** :: [Type => Str]

    Controls the placement of labels along the quoted lines.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **cut** :: [Type => Str | Number]         $Arg = [cut[unit]][+z]]$

    Do not draw contours with less than cut number of points.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **skip** :: [Type => Str | []]            $Arg = [p|t]$

    Skip all input xyz points that fall outside the region (Used when input data is a table).
  * **S** | **smooth** :: [Type => Number]

    Used to resample the contour lines at roughly every (gridbox_size/smoothfactor) interval.   (Used when input data is a grid)
  * **T** | **ticks** :: [Type => Str]                 $Arg = [+|-][+a][+dgap[/length]][+l[labels]]$

    Draw tick marks pointing in the downward direction every *gap* along the innermost closed contours.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **pen** :: [Type => Str | Number]

    Sets the attributes for the particular line.
  * **Z** | **xyz** | **triplets** :: [Type => Bool]
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

## Examples

```julia
    G = GMT.peaks();
    C = makecpt(T=(-7,9,2));

    contourf(G, show=1)
    contourf(G, C=[-2, 0, 2, 5], show=1)
    contourf(G, C, contour=[-2, 0, 2, 5], show=1)
    contourf(G, C, annot=[-2, 0, 2, 5], show=1)
    contourf(G, C, annot=2, show=1)
    contourf(G, C, contour=1, annot=[-2, 0, 2, 5], show=1)
    contourf(G, C, annot=:none, show=1)

    d = [0 2 5; 1 4 5; 2 0.5 5; 3 3 9; 4 4.5 5; 4.2 1.2 5; 6 3 1; 8 1 5; 9 4.5 5];
    contourf(d, limits=(-0.5,9.5,0,5), pen=0.25, labels=(line=(:min,:max),), show=1)
```
