```
scatter(cmd0::String="", arg1=nothing; kwargs...)
```

Reads (x,y) pairs and plot symbols at those locations on a map. This module is a subset of $plot$ to make it simpler to draw scatter plots. So many of its (fine) controling parameters are not listed here. For a finer control, user should consult the $plot$ module.

## Parameters

  * **G** | **fill** | **markerfacecolor** :: [Type => Str]

    Select color or pattern for filling of symbols or polygons.
  * **N** | **noclip** | **no_clip** :: [Type => Str | []]

    Do NOT clip symbols that fall outside map border
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **S** :: [Type => Str]

    Plot symbols (including vectors, pie slices, fronts, decorated or quoted lines). 

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

```
and select their sizes with the **markersize** or **size** keyword [default is 8p].
The marker size can be a scalar or a vector with same size numeber of rows of data. Units are
points unless specified otherwise with (for example for cm) *par=(PROJ_LENGTH_UNIT=:c,)*
```

  * **W** | **pen** | **markeredgecolor** | **mec** :: [Type => Str]

    Set pen attributes for lines or the outline of symbols
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

[`GMT man page`](http://docs.generic-mapping-tools.org/latest/plot.html)
