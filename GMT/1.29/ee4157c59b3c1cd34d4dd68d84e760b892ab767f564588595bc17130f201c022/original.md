```
sphtriangulate(cmd0::String="", arg1=nothing, kwargs...)
```

Delaunay or Voronoi construction of spherical lon,lat data

See full GMT (not the `GMT.jl` one) docs at [`sphtriangulate`](http://docs.generic-mapping-tools.org/latest/sphtriangulate.html)

## Parameters

  * **A** | **area** :: [Type => Bool]

    Compute the area of the spherical triangles (Qd) or polygons (Qv) and write the areas in the output segment headers
  * **C** | **save_mem** :: [Type => Bool]

    For large data sets you can save some memory (at the expense of more processing).
  * **D** | **skipdup** :: [Type => Bool]

    Delete any duplicate points [Default assumes there are no duplicates].
  * **L** | **unit** :: [Type => Str]          $Arg = e|f|k|m|n|u|d$

    Specify the unit used for distance and area calculations.
  * **N** | **nodes** :: [Type => Str]         $Arg = `file$

    Write the information pertaining to each polygon to a separate file.
  * **Q** | **voronoi** :: [Type => Str]     $Arg = d|v$

    Append d for Delaunay triangles or v for Voronoi polygons [Delaunay].
  * **T** | **arcs** :: [Type => Bool | Str]

    Write the unique arcs of the construction [Default writes fillable triangles or polygons].   When used with -A we store arc length in the segment header in chosen unit.
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
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? sphtriangulate$
