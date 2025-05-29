```
ternary(cmd0="", arg1=nothing; image=false, clockwise=false, kwargs...)
```

Reads (a,b,c[,z]) records from table [or file] and plots image and symbols at those locations on a ternary diagram.

  * **B** | **frame** :: [Type => NamedTuple | Str] –

    For ternary diagrams the three sides are referred to as a (bottom), b (right), and c (left). The default is to   annotate and draw grid lines but without labeling the axes. But since labeling is a very important feature, you   can use the `labels` option that take as argument a 3 elements Tuple with the labels of the 3 axes. Further   control on annotations and grid spacing (on/off) is achieved by using the `frame=(annot=?, grid=?, alabel=?, blabel=?,   clabel=?, suffix=?)` form. Note that not all options of the general `frame` options are accepted in this module and for more   elaborated frame option selection you will have to resort to the pure GMT syntax in the form `frame="<arg> <arg> <arg>"`
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    Give a CPT name or specify -Ccolor1,color2[,color3,...] to build a linear continuous CPT from those   colors automatically.
  * **G** | **fill** :: [Type => Str] –

    Select color or pattern for filling the bars
  * **L** | **vertex_labels** :: [Type => Str | Tuple of strings] –		`Arg = a/b/c`

    Set the labels for the three diagram vertices where the component is 100% [none].
  * **M** | **dump** :: [Type => Str]

    Dumps the converted input (a,b,c[,z]) records to Cartesian (x,y,[,z]) records, where x, y   are normalized coordinates on the triangle (i.e., 0–1 in x and 0–sqrt(3)/2 in y). No plotting occurs.
  * **N** | **no_clip** | **noclip** :: [Type => Str or []]

    Do NOT clip symbols that fall outside map border
  * **R** | **region** | **limits** :: [Type => Tuple | Str]

    Give the min and max limits for each of the three axis a, b, and c. Default is (0,100,0,100,0,100)
  * **S** | **symbol** :: [Type => Str]

    Plot individual symbols in a ternary diagram. If `S` is not given then we will instead plot lines   (requires `pen`) or polygons (requires `color` or `fill`). 

    Alternatively select a sub-set of symbols using the aliases: **symbol** or **marker** and values:

      * **-**, **x_dash**
      * **+**, **plus**
      * **a**, *, **star**
      * **c**, **circle**
      * **d**, **diamond**
      * **g**, **octagon**
      * **h**, **hexagon**
      * **i**, **v**, **inverted_tri**
      * **n**, **pentagon**
      * **p**, **.**, **point**
      * **r**, **rectangle**
      * **s**, **square**
      * **t**, **^**, **triangle**
      * **x**, **cross**
      * **y**, **y_dash**

    and select their sizes with the **markersize** or **size** keyword [default is 8p].   The marker size can be a scalar or a vector with same size numeber of rows of data. Units are   points unless specified otherwise with (for example for cm) *par=(PROJ*LENGTH*UNIT=:c,)*
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **pen** :: [Type => Str | Number]

    Sets the attributes for the particular line.
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    Shift plot origin relative to the current origin by (x-shift,y-shift) and optionally   append the length unit (c, i, or p).
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    Examine the spacing between consecutive data points in order to impose breaks in the line.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    Selects perspective view and sets the azimuth and elevation of the viewpoint [180/90].
  * **q** | **inrow** | **inrows** :: [Type => Str]       $Arg = [i|o][~]rows[+ccol][+a|f|s]$

    Select specific data rows to be read (-qi [Default]) or written (-qo) [all].
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    Set PDF transparency level for an overlay, in (0-100] percent range. [Default is 0, i.e., opaque].
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

Other than the above options, the `kwargs` input accepts still the following options

  * `image`: - Fills the ternary plot with an image computed automatically with `grdimage` from a grid interpolated with `surface`
  * `contour`: - This option works in two different ways. If used together with `image` it overlays a contour              by doing a call to `grdcontour`. However, if used alone it will call `contour` to do the contours.              The difference is important because this option can be used in *default mode* with `contour=true`              where the number and annotated contours is picked automatically, or the use can exert full control              by passing as argument a NamedTuple with all options appropriated to that module. *e.g.*              `contour=(cont=10, annot=20, pen=0.5)`
  * `contourf`: - Works a bit like the *standalone* `contour`. If used with `contourf=true` call make a filled contour               using automatic parameters. The form `contourf=(...)` let us selects options of the contourf module.
  * `clockwise`: - Set it to `true` to indicate that positive axes directions be clock-wise                [Default lets the a, b, c axes be positive in a counter-clockwise direction].
