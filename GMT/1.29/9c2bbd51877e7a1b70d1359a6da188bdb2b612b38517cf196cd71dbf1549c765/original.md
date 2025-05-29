```
clip(cmd0::String="", arg1=nothing; kwargs...)
```

Reads (length,azimuth) pairs from file and plot a windclip diagram.

## Parameters

  * **C** | **endclip** :: [Type => Bool]

    Mark end of existing clip path. No input file is needed.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **A** | **steps** :: [Type => Str or []]

    By default, geographic line segments are connected as great circle arcs. To connect them as straight lines, use **A**
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **N** | **invert** :: [Type => Bool]

    Invert the sense of the test, i.e., clip regions where there is data coverage.
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **T** | **clipregion** :: [Type => Bool]

    Rather than read any input files, simply turn on clipping for the current map region.

To see the full documentation type: $@? clip$
