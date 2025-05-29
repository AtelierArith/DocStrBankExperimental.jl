```
surface(cmd0::String="", arg1=nothing; kwargs...)
```

Reads randomly-spaced (x,y,z) triples and produces a binary grid file of gridded values z(x,y) by solving:

```
	(1 - T) * L (L (z)) + T * L (z) = 0
```

See full GMT (not the `GMT.jl` one) docs at [`surface`](http://docs.generic-mapping-tools.org/latest/surface.html)

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **A** | **aspect_ratio** :: [Type => Number]

    Aspect ratio. If desired, grid anisotropy can be added to the equations.
  * **C** | **convergence** :: [Type => Number]

    Convergence limit. Iteration is assumed to have converged when the maximum absolute change in any   grid value is less than convergence_limit.
  * **D** | **breakline** :: [Type => String | NamedTuple]     `Arg = breakline[+z[level]] | (data=Array, [zlevel=x])`

    Use xyz data in the breakline file as a ‘soft breakline’, that is a line whose vertices will be used to   constrain the nearest grid nodes without any further interpolation.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = surface(....) form.
  * **Ll** | **lower** :: [Type => Str | Number]

    Impose limits on the output solution. lower sets the lower bound. lower can be the name of a grid   file with lower bound values, a fixed value, d to set to minimum input value,
  * **Lu** | **upper** :: [Type => Str | Number]
  * **M** | **mask** :: [Type => Number]      `Arg = max_radius`

    After solving for the surface, apply a mask so that nodes farther than max_radius away from a data constraint is set to NaN.
  * **N** | **iterations** | **max_iterations** :: [Type => Number]

    Number of iterations. Iteration will cease when convergence*limit is reached or when number of   iterations reaches max*iterations.
  * **Q** | **suggest** :: [Type => Bool]

    Suggest grid dimensions which have a highly composite greatest common factor.
  * **S** | **search_radius** :: [Type => Number | Str]  

    Sets the resolution of the projected grid that will be created.
  * **T** | **tension** :: [Type => Number | Str]

    Tension factor[s]. These must be between 0 and 1.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **log** :: [Type => Str]

    Write convergence information to a log file [surface_log.txt].
  * **Z** | **over_relaxation** :: [Type => Str | GMTgrid]

    Over-relaxation factor. This parameter is used to accelerate the convergence; it is a number between 1 and 2.
  * **preproc** :: [Type => Bool | Str/Symb]

    This option means that the data is previously passed through one of $block*$ modules to decimate the data   in each cell as strongly advised. `preproc=true` will use $blockmean$. To use any of the other two,   pass its name as value. *e.g.* `preproc="blockmedian"`.
  * **a** | **aspatial** :: [Type => Str]			$Arg = [col=]name[…]$

    Control how aspatial data are handled in GMT during input and output.
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary format for primary input (secondary inputs are always ASCII).
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    Examine all input columns and if any item equals nodata we interpret this value as a   missing data item and substitute the value NaN.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? surface$
