```
grdvector(arg1, arg2, kwargs...)
```

Takes two 2-D grid files which represents the x- and y-components of a vector field and produces a vector field plot by drawing vectors with orientation and length according to the information in the files. Alternatively, polar coordinate r, theta grids may be given instead.

See full GMT (not the `GMT.jl` one) docs at [`grdvector`](http://docs.generic-mapping-tools.org/latest/grdvector.html)

## Parameters

  * **A** | **polar** :: [Type => Bool]  

    The grid contain polar (r, theta) components instead of Cartesian (x, y) [Default is Cartesian components].
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **G** | **fill** :: [Type => Str | Number]

    Sets color or shade for vector interiors [Default is no fill].
  * **I** | **inc** | **increment** | **spacing** :: [Type => Sytr | Number]	$Arg=[x]dx[/dy]$

    Only plot vectors at nodes every x*inc, y*inc apart (must be multiples of original grid spacing).
  * **maxlen** :: [Type => Number]

    Set the maximum length in plot units that an arrow will have. By default it's equal to fig width / 20.

```
This option is ignored if **inc** is set.
```

  * **N** | **noclip** | **no_clip** :: [Type => Bool]

    Do NOT clip symbols that fall outside map border
  * **Q** | **vec** | **vector** | **arrow** :: [Type => Str]

    Modify vector parameters. For vector heads, append vector head size [Default is 0, i.e., stick-plot].
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **vscale** | **vec_scale** :: [Type => Str | Number]		$Arg = [i|l]scale[unit]$

    Sets scale for vector plot length in data units per plot distance measurement unit [1].
  * **T** | **sign_scale** :: [Type => Bool]

    Means the azimuths of Cartesian data sets should be adjusted according to the signs of the   scales in the x- and y-directions [Leave alone].
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **pen** :: [Type => Str | Number]

    Sets the attributes for the particular line.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **Z** | **azimuth** :: [Type => Bool]

    The theta grid provided contains azimuths rather than directions (implies -A).
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

To see the full documentation type: $@? grdvector$
