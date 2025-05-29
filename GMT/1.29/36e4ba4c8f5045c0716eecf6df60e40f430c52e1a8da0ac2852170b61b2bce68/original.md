```
colorbar(arg1=nothing; kwargs...)
```

Plots gray scales or color scales on maps.

  * **D** | **pos** | **position** :: [Type => Str]

    Defines the reference point on the map for the color scale using one of four coordinate systems.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **F** | **box** :: [Type => Str]

    Draws a rectangular border around the scale.
  * **G** | **truncate** :: [Type => Str]  

    Truncate the incoming CPT so that the lowest and highest z-levels are to zlo and zhi.
  * **I** | **shade** :: [Type => Number | Str]

    Add illumination effects.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **equal** | **equal_size** :: [Type => Str | Bool]		`Arg = [i][gap]`

    Gives equal-sized color rectangles. Default scales rectangles according to the z-range in the CPT.
  * **M** | **monochrome** :: [Type => Bool]

    Force conversion to monochrome image using the (television) YIQ transformation.
  * **N** | **dpi** :: [Type => Str | Number]

    Controls how the color scale is represented by the PostScript language.
  * **Q** | **log** :: [Type => Str]

    Selects a logarithmic interpolation scheme [Default is linear].
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **appearance** | **nolines** :: [Type => Bool | []]

    Do not separate different color intervals with black grid lines.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **scale** :: [Type => Number]

    Multiply all z-values in the CPT by the provided scale.
  * **Z** | **zfile** :: [Type => Str]

    File with colorbar-width per color entry.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? colorbar$
