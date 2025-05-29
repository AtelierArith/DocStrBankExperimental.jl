```
meca(cmd0::String="", arg1=nothing; kwargs...)
```

Plot focal mechanisms.

See full GMT (not the `GMT.jl` one) docs at [`meca`](http://docs.generic-mapping-tools.org/latest/supplements/seis/meca.html)

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **A** | **offset** :: [Type => Bool | Str | GMTcpt]

    Offsets focal mechanisms to the longitude, latitude specified in the last two columns of the input
  * **C** | **color** | **cmap** :: [Type => Number | Str | GMTcpt]

    Give a CPT and let compressive part color be determined by the z-value in the third column.
  * **D** | **depth_limits** :: [Type => Str | Tuple]

    Plots events between depmin and depmax.
  * **E** | **fill_extensive** | **extensionfill** :: [Type => Str | Number]

    Selects filling of extensive quadrants. [Default is white].
  * **Fa** | **Fe** | **Fg** | **Fo** | **Fp** | **Fr** | **Ft** | **Fz** :: [Type => ]

    Sets one or more attributes.
  * **G** | **fill** | **compressionfill** :: [Type => Str | Number]

    Selects shade, color or pattern for filling the sectors [Default is no fill].
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **L** | **outline_pen** | **pen_outline** :: [Type => Str | Number | Tuple]

    Draws the “beach ball” outline with pen attributes instead of with the default pen set by **pen**
  * **M** | **same_size** | **samesize** :: [Type => Bool]

    Use the same size for any magnitude. Size is given with **S**
  * **N** | **no_clip** | **noclip** :: [Type => Str | []]

    Do NOT skip symbols that fall outside frame boundary.
  * **Sc|aki** | **Sc|CMT|gcmt** | **Sm|mt|moment_tensor** | ... :: [Type => Str]

    Selects the meaning of the columns in the input data.
  * **convention=:Sa|:aki|:Sc|:CMT|:gcmt|:Sm|:mt|:moment*tensor|:Sd|:mt*closest|:moment*closest|:Sz|:mt*deviatoric :moment*deviatoric|:Sp :partial|:Sx|:principal|:principal*axis|:Sy|:principal*closest|:St|:principal*deviatoric

    Alternative way of selecting the meaning of the columns in the input data.
  * **T** | **nodal** :: [Type => Number | Str]

    Plots the nodal planes and outlines the bubble which is transparent.
  * **W** | **pen** :: [Type => Str | Tuple]

    Set pen attributes for all lines and the outline of symbols.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    Selects perspective view and sets the azimuth and elevation of the viewpoint [180/90].
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

Example: Plot a focal mechanism using the Aki & Richards convention 

```julia
    psmeca([0.0 3.0 0.0 0 45 90 5 0 0], aki=true, fill=:black, region=(-1,4,0,6), proj=:Merc, show=1)
```

The same but add a Label

```julia
    psmeca(mat2ds([0.0 3.0 0.0 0 45 90 5 0 0], ["Thrust"]), aki=true, fill=:black, region=(-1,4,0,6), proj=:Merc, show=1)
```
