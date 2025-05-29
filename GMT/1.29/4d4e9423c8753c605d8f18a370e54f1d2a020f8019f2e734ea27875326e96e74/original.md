```
grdrotater(cmd0::String="", arg1=nothing; kwargs...)
```

Takes a geographical grid and reconstructs it given total reconstruction rotations.

See full GMT (not the `GMT.jl` one) docs at [`grdrotater`](http://docs.generic-mapping-tools.org/latest/supplements/spotter/grdrotater.html)

## Parameters

  * **A** | **rot_region** :: [Type => Str | Tuple | Vec]

    Specify directly the region of the rotated grid.
  * **D** | **rot_outline** :: [Type => Bool or Str]	$Arg = true | filename$

    Name of the grid polygon outline file. This represents the outline of the grid reconstructed to the specified time.
  * **F** | **rot_polyg** | **rot_polygon** :: [Type => Str | GMTdaset | Mx2 array]	$Arg = filename | dataset)$

    Specify a multisegment closed polygon file that describes the inside area of the grid that should be rotated.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdrotater(....) form.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **T** | **ages** :: [Type => Str | Tuple]

    Sets the desired reconstruction times. For a single time append the desired time.   (http://docs.generic-mapping-tools.org/latest/grdrotater.html#t)
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    Examine the spacing between consecutive data points in order to impose breaks in the line.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Select grid interpolation mode by adding b for B-spline smoothing, c for bicubic interpolation,   l for bilinear interpolation, or n for nearest-neighbor value.
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.

### Example

```julia
G = grdmath("-R-5/5/-5/5 -I0.1 -fg X Y HYPOT");
tri = [-2.411 -1.629; -0.124 2.601; 2.201 -1.629; -2.410 -1.629];
Gr, tri_rot = grdrotater(G, rotation="-40.8/32.8/-12.9", rot_outline=true, rot_polygon=tri);
imshow(Gr, plot=(data=tri_rot,))
```
