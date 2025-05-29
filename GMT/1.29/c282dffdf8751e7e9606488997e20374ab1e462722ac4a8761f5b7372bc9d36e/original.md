```
project(cmd0::String="", arg1=nothing, kwargs...)
```

Project data onto lines or great circles, generate tracks, or translate coordinates.

See full GMT (not the `GMT.jl` one) docs at [`project`](http://docs.generic-mapping-tools.org/latest/project.html)

## Parameters

  * **C** | **origin** | **start_point** :: [Type => list/tuple]    $Arg = (x,y)$

    Sets the origin of the projection, in Definition 1 or 2.
  * **A** | **azim** | **azimuth** :: [Type => Number]    $Arg = azimuth$

    Defines the azimuth of the projection (Definition 1).
  * **E** | **end_pt** | **endpoint** :: [Type => list/tuple]    $Arg = (bx,by)$

    bx,by defines the end point of the projection path (Definition 2).
  * **F** | **outvars** :: [Type => Str]    $Arg = xyzpqrs$

    Specify your desired output using any combination of xyzpqrs, in any order [Default is xyzpqrs].
  * **G** | **step** | **generate** :: [Type => Number or list/tuple–    $Arg = dist[/colat][+h]$

    Generate mode. No input is read. Create (r, s, p) output points every dist units of p. See Q option.
  * **L** | **length** :: [Type => Number or list/tuple]    $Arg = [w|l_{min}/l_{max}]$

    Length controls. Project only those points whose p coordinate is within l_min < p < l_max.
  * **N** | **flat_earth** :: [Type => Bool or []]

    Flat Earth. Make a Cartesian coordinate transformation in the plane. [Default uses spherical trigonometry.]
  * **Q** | **km** :: [Type => Bool or []]

    Map type units.
  * **S** | **sort** :: [Type => Bool or []]

    Sort the output into increasing p order. Useful when projecting random data into a sequential profile.
  * **T** | **pole** :: [Type => list/tuple]    $Arg = (px,py)$

    px,py sets the position of the rotation pole of the projection. (Definition 3).
  * **W** | **width** :: [Type => list/tuple]    $Arg = (w_{min},w_{max})$

    Width controls. Project only those points whose q coordinate is within w_min < q < w_max.
  * **Z** | **ellipse** :: [Type => Number | Tuple | String]    $Arg = major/minor/azimuth[+e|n]$

    Make ellipse with major and minor axes given in km (unless **N** is given for a Cartesian ellipse) and the   azimuth of the major axis in degrees; used in conjunction with **origin** (sets its center) and **step**   (sets the distance increment).
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.
  * **append** :: [Type => Str]     $Arg = fname$

    Append result to an existing file named $fname$ instead of returning to a Julia variable.   Use the bo option to save as a binary file.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
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
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    Suppress output for records whose z-value equals NaN.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? project$
