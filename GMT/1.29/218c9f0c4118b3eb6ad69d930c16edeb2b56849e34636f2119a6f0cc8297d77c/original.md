```
gmtselect(cmd0::String="", arg1=nothing, kwargs...)
```

Select data table subsets based on multiple spatial criteria.

See full GMT (not the `GMT.jl` one) docs at [`gmtselect`](http://docs.generic-mapping-tools.org/latest/gmtselect.html)

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **A** | **area** :: [Type => Str | Number]

    Features with an area smaller than min*area in km^2 or of hierarchical level that is   lower than min*level or higher than max_level will not be plotted.
  * **C** | **dist2pt** | **dist** :: [Type => Str | NamedTuple]   `Arg = pointfile+ddist[unit] | (pts=Array, dist=xx)`

    Pass all records whose location is within dist of any of the points in the ASCII file pointfile.   If dist is zero then the 3rd column of pointfile must have each point’s individual radius of influence.
  * **D** | **res** | **resolution** :: [Type => Str]      `Arg = c|l|i|h|f`

    Ignored unless N is set. Selects the resolution of the coastline data set to use   ((f)ull, (h)igh, (i)ntermediate, (l)ow, or (c)rude).
  * **E** | **boundary** :: [Type => Str | []]            `Arg = [fn]`

    Specify how points exactly on a polygon boundary should be considered.
  * **F** | **polygon** :: [Type => Str | GMTdaset | Mx2 array]     `Arg = polygonfile`

    Pass all records whose location is within one of the closed polygons in the multiple-segment   file $polygonfile$ or a GMTdataset type or a Mx2 array defining the polygon.
  * **G** | **gridmask** :: [Type => Str | GRDgrid]        `Arg = gridmask`

    Pass all locations that are inside the valid data area of the grid gridmask.   Nodes that are outside are either NaN or zero.
  * **I** | **invert** | **reverse** :: [Type => Str | []]    `Arg = [cflrsz]`

    Reverses the sense of the test for each of the criteria specified.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **L** | **dist2line** :: [Type => Str | NamedTuple]    `Arg = linefile+ddist[unit][+p] | (pts=Array, dist=xx, ortho=_)`

    Pass all records whose location is within dist of any of the line segments in the ASCII   multiple-segment file linefile.
  * **N** | **mask** :: [Type => Str | List]     `Arg = ocean/land/lake/island/pond or wet/dry`

    Pass all records whose location is inside specified geographical features.
  * **Z** | **in_range** :: [Type => Str | List]     `Arg = min[/max][+a][+ccol][+i]`

    Pass all records whose 3rd column (z; col = 2) lies within the given range or is NaN.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.
  * **append** :: [Type => Str]     $Arg = fname$

    Append result to an existing file named $fname$ instead of returning to a Julia variable.   Use the bo option to save as a binary file.
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
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
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.
