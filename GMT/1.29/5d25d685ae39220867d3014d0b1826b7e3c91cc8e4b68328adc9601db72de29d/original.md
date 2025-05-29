```
mbimport(cmd0::String="", arg1=nothing, arg2=nothing, arg3=nothing; kwargs...)
```

Produces a gray-shaded (or colored) map by plotting rectangles centered on each grid node and assigning them a gray-shade (or color) based on the z-value.

## Parameters

  * **A** | **footprint** :: [Type => Str | Tuple]	$Arg = factor/mode/depth$

    Determines how the along-track dimension of the beam or pixel footprints is calculated.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **D** | **scaling** :: [Type => Str | Tuple]	$Arg = mode/scale/min/max$

    Sets scaling of beam amplitude or sidescan pixel values which can be applied before plotting.
  * **E** | **dpi** :: [Type => Int]

    Sets the resolution of the projected image that will be created.
  * **G** | **bit_color** :: [Type => Str | Tuple]	$Arg = magnitude/azimuth or magnitude/median$

    Sets the parameters controlng simulated illumination of bathymetry.
  * **S** | **speed** :: [Type => Number]

    Sets the minimum speed in km/hr (5.5 kts ~ 10 km/hr) allowed in the input data.
  * **T** | **timegap** :: [Type => number]

    Sets the maximum time gap in minutes between adjacent pings before being considered a gap.
  * **Z** | **type_plot** :: [Type => Str | Number]

    Sets the style of the plot.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Select grid interpolation mode by adding b for B-spline smoothing, c for bicubic interpolation,   l for bilinear interpolation, or n for nearest-neighbor value.
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
