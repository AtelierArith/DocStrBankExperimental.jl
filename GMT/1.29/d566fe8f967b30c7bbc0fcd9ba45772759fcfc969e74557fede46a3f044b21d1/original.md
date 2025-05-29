```
grdedit(cmd0::String="", arg1=nothing, kwargs...)
```

Reads the header information in a binary 2-D grid file and replaces the information with values provided on the command line.

If single input is a G GMTgrid object, it will update the z_min|max values of the G.range member

See full GMT (not the `GMT.jl` one) docs at [`grdedit`](http://docs.generic-mapping-tools.org/latest/grdedit.html)

## Parameters

  * **A** | **adjust_inc** :: [Type => Bool]

    If necessary, adjust the file’s x*inc, y*inc to be compatible with its domain.
  * **C** | **adjust_inc** :: [Type => Bool]

    Clear the command history from the grid header.
  * **D** | **header** | **metadata** :: [Type => Str]    $Arg = [+xxname][+yyname][+zzname][+sscale][+ooffset][+ninvalid][+ttitle][+rremark$

    Change these header parameters.
  * **E** | **flip** :: [Type => Str]    $Arg = [a|h|l|r|t|v]$

    Transform the grid in one of six ways and (for l|r|t) interchange the x and y information
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdedit(....) form.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **N** | **replace** :: [Type => Str | Mx3 array]      $Arg = replace=fname | replace=Array$

    Read the ASCII (or binary) file table and replace the corresponding nodal values in the   grid with these x,y,z values. Alternatively, provide a Mx3 matrix with values to be changed.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **wrap** :: [Type => Bool]

    For global, geographical grids only. Grid values will be shifted longitudinally according to   the new borders given in $limits$ (R option).
  * **T** | **toggle_reg** | **toggle** :: [Type => Bool]

    Make necessary changes in the header to convert a gridline-registered grid to a pixel-registered   grid, or vice-versa.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.
