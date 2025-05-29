```
logo(cmd0::String=""; kwargs...)
```

Plots the GMT logo on a map. By default, the GMT logo is 5 cm wide and 2.5 cm high and will be positioned relative to the current plot origin. Use various options to change this and to place a transparent or opaque rectangular map panel behind the GMT logo.

See full GMT (not the `GMT.jl` one) docs at [`gmtlogo`](http://docs.generic-mapping-tools.org/latest/gmtlogo.html)

## Parameters

  * **D** | **pos** | **position** :: [Type => Str]

    Sets reference point on the map for the image using one of four coordinate systems.
  * **F** | **box** :: [Type => Str]

    Without further options, draws a rectangular border around the GMT logo using `MAP_FRAME_PEN`.   or map rose (T)
  * **julia** :: [Type => Number]

    Create the Julia instead of the GMT logo. Provide circle diameter in centimeters
  * **GMTjulia** :: [Type => Number]

    Create the GMT Julia GMT logo. Provide circle diameter in centimeters
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")
  * Example, make a GMT Julia logo with circles of 1 cm: logo(GMTjulia=1, show=true)
