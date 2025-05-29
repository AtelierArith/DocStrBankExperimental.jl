```
grd2xyz(cmd0::String="", arg1=nothing, kwargs...)
```

Reads one 2-D grid and returns xyz-triplets.

See full GMT (not the `GMT.jl` one) docs at [`grd2xyz`](http://docs.generic-mapping-tools.org/latest/grd2xyz.html)

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **C** | **row_col** | **rowcol** :: [Type => Bool]

    Replace the x- and y-coordinates on output with the corresponding column and row numbers.
  * **L** | **hvline** :: [Type => String]

    Limit the output of records to a single row or column.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **T** | **stl** | **STL** :: [Type => String]

    Compute a STL triangulation for 3-D printing.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **weight** :: [Type => Str]           `Arg = [a|weight]`

    Write out x,y,z,w, where w is the supplied weight (or 1 if not supplied) [Default writes x,y,z only].
  * **Z** | **onecol** | **one_col** :: [Type => Str]

    Write a 1-column table. Output will be organized according to the specified ordering   convention contained in $flags$.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.
  * **append** :: [Type => Str]     $Arg = fname$

    Append result to an existing file named $fname$ instead of returning to a Julia variable.   Use the bo option to save as a binary file.
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary output.
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    Suppress output for records whose z-value equals NaN.
