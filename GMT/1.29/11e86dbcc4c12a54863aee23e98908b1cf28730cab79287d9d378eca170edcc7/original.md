```
image(cmd0::String="", arg1=nothing; kwargs...)
```

Place images or EPS files on maps.

See full GMT (not the `GMT.jl` one) docs at [`psimage`](http://docs.generic-mapping-tools.org/latest/image.html)

## Parameters

  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **D** | **pos** | **position** :: [Type => Str]

    Sets reference point on the map for the image using one of four coordinate systems.
  * **F** | **box** :: [Type => Str | []]

    Without further options, draws a rectangular border around the image using MAP*FRAME*PEN.
  * **G** | **bitcolor** | **bit_color** | **bit_bg|fg|alpha**:: [Type => Str]

    Change certain pixel values to another color or make them transparent.
  * **I** | **invert** :: [Type => Str | Number]

    Invert 1-bit image before plotting.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **M** | **monochrome** :: [Type => Bool]

    Convert color image to monochrome grayshades using the (television) YIQ-transformation.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    Selects perspective view and sets the azimuth and elevation of the viewpoint [180/90].
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? image$
