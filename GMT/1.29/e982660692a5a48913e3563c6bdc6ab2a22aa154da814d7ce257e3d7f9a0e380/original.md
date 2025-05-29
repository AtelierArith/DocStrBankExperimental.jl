```
grdvolume(cmd0::String="", arg1=nothing, kwargs...)
```

Reads one 2-D grid and returns xyz-triplets.

See full GMT (not the `GMT.jl` one) docs at [`grdvolume`](http://docs.generic-mapping-tools.org/latest/grdvolume.html)

## Parameters

  * **C** | **cont** | **contour** :: [Type => Str | List]   $Arg = cval or low/high/delta or rlow/high or rcval$

    Find area, volume and mean height (volume/area) inside the cval contour.
  * **L** | **base_level** :: [Type => Number]          $Arg = base$

    Also add in the volume from the level of the contour down to base [Default base is contour].
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **unit** :: [Type => Str]              $Arg = e|f|k|M|n|u$

    For geographical grids, append a unit from e|f|k|M|n|u [Default is meter (e)].
  * **T** :: [Type => Str]                        $Arg = [c|h]$

    Determine the single contour that maximized the average height (= volume/area).
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **Z** | **scale** :: [Type => Str or List]     $Arg = fact[/shift]$

    Optionally subtract shift before scaling data by fact. [Default is no scaling].
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.

To see the full documentation type: $@? grdvolume$
