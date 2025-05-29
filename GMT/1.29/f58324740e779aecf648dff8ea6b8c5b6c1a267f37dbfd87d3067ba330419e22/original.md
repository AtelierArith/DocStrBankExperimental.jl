```
grdfill(cmd0::String="", arg1=nothing, kwargs...)
```

Reads a grid that presumably has unfilled holes that the user wants to fill in some fashion. Holes are identified by NaN values but this criteria can be changed.

See full GMT (not the `GMT.jl` one) docs at [`grdfill`](http://docs.generic-mapping-tools.org/latest/grdfill.html)

## Parameters

  * **A** | **mode** :: [Type => Str]		$Arg = mode[arg]$

    Specify the hole-filling algorithm to use. Choose from c for constant fill and append the constant value,   n for nearest neighbor (and optionally append a search radius in pixels).
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdfill(....) form.
  * **L** | **list** :: [Type => Str]	$Arg = [p]$

    Just list the rectangular subregions west east south north of each hole. No grid fill takes place and   **outgrid** is ignored. Optionally, append **p** to instead write closed polygons for all subregions.
  * **N** | **nodata** :: [Type => Str]	$Arg = nodata$

    Sets the node value that identifies a point as a member of a hole [Default is NaN].
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
