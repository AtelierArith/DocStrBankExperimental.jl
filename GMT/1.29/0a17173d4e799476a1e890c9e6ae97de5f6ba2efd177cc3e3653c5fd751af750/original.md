```
gmtsplit(cmd0::String="", arg1=nothing; kwargs...)
```

Reads a series of (x,y[,z]) records [or optionally (x,y,z,d,h)] and splits this into separate lists of (x,y[,z]) series, such that each series has a nearly constant azimuth through the x,y plane.

See full GMT (not the `GMT.jl` one) docs at [`gmtsplit`](http://docs.generic-mapping-tools.org/latest/gmtsplit.html)

## Parameters

  * **A** | **azim_tol** :: [Type => Str | Array]  

    Write out only those segments which are within +/- tolerance degrees of azimuth in heading,   measured clockwise from North, [0 - 360].
  * **C** | **course_change** :: [Type => Number]

    Terminate a segment when a course change exceeding course_change degrees of heading is detected.
  * **D** | **min_dist** | **min_distance** :: [Type => Number]

    Do not write a segment out unless it is at least minimum_distance units long.
  * **F** | **filter** :: [Type => Str | Array]

    Filter the z values and/or the x,y values, assuming these are functions of d coordinate.   xy*filter and z*filter are filter widths in distance units.
  * **N** | **multi** | **multifile** :: [Type => Bool | Str]

    Write each segment to a separate output file.
  * **Q** | **fields** :: [Type => Str]

    Specify your desired output using any combination of xyzdh, in any order.
  * **S** | **dh** | **dist_head** :: [Type => Bool]

    Both d and h are supplied. In this case, input contains x,y,z,d,h. [Default expects (x,y,z) input,   and d,h are computed from delta x, delta y.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.
  * **append** :: [Type => Str]     $Arg = fname$

    Append result to an existing file named $fname$ instead of returning to a Julia variable.   Use the bo option to save as a binary file.
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary output.
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    Examine all output columns and if any item equals NAN substitute it with   the chosen missing data value.
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
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? splitxyz$
