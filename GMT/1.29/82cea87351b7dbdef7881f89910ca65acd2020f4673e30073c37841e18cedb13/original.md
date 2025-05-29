```
grdlandmask([monolithic::String="";] area=, resolution=, bordervalues=, save=, maskvalues=, registration=, verbose=, cores=)
```

Create a grid file with set values for land and water.

Read the selected shoreline database and create a grid to specify which nodes in the specified grid are over land or over water. The nodes defined by the selected region and lattice spacing will be set according to one of two criteria: (1) land vs water, or (2) the more detailed (hierarchical) ocean vs land vs lake vs island vs pond.

See full GMT (not the `GMT.jl` one) docs at [`grdlandmask`](http://docs.generic-mapping-tools.org/latest/grdlandmask.html)

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **A** | **area** :: [Type => Str | Number]

    Features with an area smaller than min*area in km^2 or of hierarchical level that is lower than min*level   or higher than max_level will not be plotted.
  * **D** | **res** | **resolution** :: [Type => Str]

    Selects the resolution of the data set to use ((f)ull, (h)igh, (i)ntermediate, (l)ow, and (c)rude).
  * **E** | **border** | **bordervalues** :: [Type => Str | List]    $Arg = cborder/lborder/iborder/pborder or bordervalue$

    Nodes that fall exactly on a polygon boundary should be considered to be outside the polygon   [Default considers them to be inside].
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdlandmask(....) form.
  * **N** | **maskvalues** | **mask** :: [Type => Str | List]    $Arg = wet/dry or ocean/land/lake/island/pond$

    Sets the values that will be assigned to nodes. Values can be any number, including the textstring NaN
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    Limit the number of cores to be used in any OpenMP-enabled multi-threaded algorithms.   (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)

To see the full documentation type: $@? grdlandmask$
