```
grdinfo(cmd0::String="", arg1=nothing; kwargs...)
```

Reads a 2-D grid file and reports metadata and various statistics for the (x,y,z) data in the grid file

## Parameters

  * **C** | **oneliner** | **numeric** :: [Type => Str | Number]

    Formats the report using tab-separated fields on a single line.
  * **D** | **tiles** :: [Type => Number | Str]  

    Divide a single grid’s domain (or the -R domain, if no grid given) into tiles of size   dx times dy (set via -I).
  * **E** | **extrema** | **extreme** :: [Type => Bool]

    Report the extreme values found on a per column (E=:x) or per row (E=:y) basis.
  * **F** | **report_ingeog** :: [Type => Bool]

    Report grid domain and x/y-increments in world mapping format.
  * **G** | **download** :: [Type => Bool]

    Force (possible) download and mosaicing of all tiles of tiled global remote grids in order   to report the requested information.
  * **I** | **nearest** :: [Type => Number | Str]     $Arg = [dx[/dy]|b|i|r]$

    Report the min/max of the region to the nearest multiple of dx and dy, and output   this in the form -Rw/e/s/n
  * **L** | **force_scan** :: [Type => Number | Str]

    Report stats after actually scanning the data.
  * **M** | **minmax_pos** :: [Type => Bool]

    Find and report the location of min/max z-values.
  * **Q** | **cube** :: [Type => Bool]

    Input files must be data 3-D netCDF data cube. Not compatible with **D**, **E**, **F**, and **Ib** (GMT6.2)
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **T** | **minmax** :: [Type => Number | Str]   Determine min and max z-value.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.

To see the full documentation type: $@? grdinfo$
