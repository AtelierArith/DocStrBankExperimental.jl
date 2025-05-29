```
coast(cmd0::String=""; kwargs...)
```

Plot continents, shorelines, rivers, and borders on maps.

Plots grayshaded, colored, or textured land-masses [or water-masses] on maps and [optionally] draws coastlines, rivers, and political boundaries. A map projection must be supplied.

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **A** | **area** :: [Type => Str or Number]

    Features with an area smaller than min*area in km^2 or of   hierarchical level that is lower than min*level or higher than   max_level will not be plotted.
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **river_fill** :: [Type => Str]

    Set the shade, color, or pattern for lakes and river-lakes.
  * **D** | **res** | **resolution** :: [Type => Str]		$Arg = c|l|i|h|f|a$

    Selects the resolution of the data set to use ((f)ull, (h)igh, (i)ntermediate, (l)ow, (c)rude), or (a)uto).
  * **E** | **DCW** :: [Type => Str]

    Select painting or dumping country polygons from the Digital Chart of the World.

      * Tuple("code", Str); Tuple(code, number); Tuple("code" [,"fill"], (pen)); Tuple((...),(...),...)
      * ex: ("PT",(0.5,"red","–")); (("PT","gblue",(0.5,"red"),("ES",(0.5,"yellow")))
      * ```
        DCW=:PT; DCW=(:PT, 1); DCW=("PT", :red)
        ```
  * **getR** | **getregion** | **get_region** :: [Type => Str]

    Return the region corresponding to the code/list-of-codes passed in as argument.
  * **F** | **box** :: [Type => Str]

    Draws a rectangular border around the map scale or rose.
  * **G** | **land** :: [Type => Str]

    Select filling or clipping of “dry” areas.
  * **I** | **rivers** :: [Type => Str]

    Draw rivers. Specify the type of rivers and [optionally] append pen attributes.
  * **L** | **map_scale** :: [Type => Str]

    Draw a map scale.
  * **M** | **dump** :: [Type => Str]

    Dumps a single multisegment ASCII output. No plotting occurs.
  * **N** | **borders** :: [Type => Str]

    Draw political boundaries. Specify the type of boundary and [optionally] append pen attributes
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **clip** :: [Type => Str]		$Arg = land|water|end$

    To clip land do *clip=:land*, *clip=:water* clips water. Use *end* to mark end of existing clip path.   No projection information is needed.
  * **S** | **water** | **ocean** :: [Type => Str]

    Select filling or clipping of “wet” areas.
  * **Td** | **rose`** :: [Type => Str]

    Draws a map directional rose on the map at the location defined by the reference and anchor points.
  * **Tm** | **compass** :: [Type => Str]

    Draws a map magnetic rose on the map at the location defined by the reference and anchor points.
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    Draw GMT time stamp logo on plot.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **shore** | **shorelines** | **coast** | **coastlines** :: [Type => Str]   Draw shorelines [Default is no shorelines]. Append pen attributes.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? coast$
