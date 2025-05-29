```
gmtspatial(cmd0::String="", arg1=nothing, kwargs...)
```

Geospatial operations on points, lines and polygons.

See full GMT (not the `GMT.jl` one) docs at [`gmtspatial`](http://docs.generic-mapping-tools.org/latest/gmtspatial.html)

## Parameters

  * **A** | **nn** | **nearest_neighbor** :: [Type => Str]     `Arg = [amin_dist][unit]`

    Perform spatial nearest neighbor (NN) analysis: Determine the nearest neighbor of each point   and report the NN distances and the point IDs involved in each pair.
  * **C** | **clip** :: [Type => Bool]

    Clips polygons to the map region, including map boundary to the polygon as needed. The result is a closed polygon.
  * **D** | **duplicates** :: [Type => Str]   `Arg = [+ffile][+aamax][+ddmax][+c|Ccmax][+sfact]`

    Check for duplicates among the input lines or polygons, or, if file is given via +f, check if the   input features already exist among the features in file.
  * **E** | **handedness** :: [Type => Str]  `Arg = +|-`

    Reset the handedness of all polygons to match the given + (counter-clockwise) or - (clockwise). Implies Q+
  * **F** | **force_polygons** :: [Type => Str | []]   `Arg = [l]`

    Force input data to become polygons on output, i.e., close them explicitly if not already closed.   Optionally, append l to force line geometry.
  * **I** | **intersections** :: [Type => Str | []]   `Arg = [e|i]`

    Determine the intersection locations between all pairs of polygons.
  * **N** | **in_polygons** | **in_polyg** :: [Type => Str]     `Arg = pfile[+a][+pstart][+r][+z]`

    Determine if one (or all, with +a) points of each feature in the input data are inside any of   the polygons given in the pfile.
  * **Q** | **centroid** or **area** or **length** :: [Type => Str]      `Arg = [[unit][+cmin[/max]][+h][+l][+p][+s[a|d]]`

    Measure the area of all polygons or length of line segments.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **polygons** :: [Type => Str]     `Arg = h|i|j|s|u`

    Spatial processing of polygons.
  * **T** | **truncate** :: [Type => Str | []]     `Arg = [clippolygon]`

    Truncate polygons against the specified polygon given, possibly resulting in open polygons.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **extend** :: [Type => Str | Tuple]     `Arg = <dist>[<unit>][+f|l]`

    Extend all segments with extra first and last points that are <dist> units away from the original   end points in the directions implied by the line ends.
