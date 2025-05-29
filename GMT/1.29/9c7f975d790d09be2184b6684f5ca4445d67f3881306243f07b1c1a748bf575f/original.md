```
triangulate(cmd0::String="", arg1=nothing; kwargs...)
```

Reads randomly-spaced x,y[,z](or file) and performs Delaunay triangulation, i.e., it finds how the points should be connected to give the most equilateral triangulation possible. 

See full GMT (not the `GMT.jl` one) docs at [`triangulate`](http://docs.generic-mapping-tools.org/latest/triangulate.html)

## Parameters

  * **A** | **area** :: [Type => Bool]

    Compute the area of the Cartesian triangles and append the areas in the output segment headers   [no areas calculated]. Requires **triangles** and is not compatible with **voronoi** (GMT >= 6.4).
  * **C** | **slope_grid** :: [Type => Number]

    Read a slope grid (in degrees) and compute the propagated uncertainty in the   bathymetry using the CURVE algorithm
  * **D** | **derivatives** :: [Type => Str]

    Take either the x- or y-derivatives of surface represented by the planar facets (only used when G is set).
  * **E** | **empty** :: [Type => Str | Number]

    Set the value assigned to empty nodes when G is set [NaN].
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Use triangulation to grid the data onto an even grid (specified with R I).   Append the name of the output grid file.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **L** | **index** :: [Type => Bool]

    Give name of file with previously computed Delaunay information. If the indexfile is binary and can be read   the same way as the binary input table then you can append +b to spead up the reading (GMT6.4).
  * **M** | **network** :: [Type => Bool]

    Output triangulation network as multiple line segments separated by a segment header record.
  * **N** | **ids** :: [Type => Bool]

    Used in conjunction with G to also write the triplets of the ids of all the Delaunay vertices
  * **Q** | **voronoi** :: [Type => Str | []]

    Output the edges of the Voronoi cells instead [Default is Delaunay triangle edges]
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **triangles** :: [Type => Bool]  

    Output triangles as polygon segments separated by a segment header record. Requires Delaunay triangulation.
  * **T** | **edges** :: [Type => Bool]

    Output edges or polygons even if gridding has been selected with the G option
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
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
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? triangulate$
