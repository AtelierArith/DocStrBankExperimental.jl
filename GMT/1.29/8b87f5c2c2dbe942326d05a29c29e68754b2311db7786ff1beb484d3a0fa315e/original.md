```
greenspline(cmd0::String="", arg1=nothing; kwargs...)
```

Reads randomly-spaced (x,y,z) triples and produces a binary grid file of gridded values z(x,y) by solving:

```
	(1 - T) * L (L (z)) + T * L (z) = 0
```

See full GMT (not the `GMT.jl` one) docs at [`greenspline`](http://docs.generic-mapping-tools.org/latest/greenspline.html)

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **I** | **inc** :: [Type => Str | Number]

    *x_inc* [and optionally *y_inc*] is the grid spacing.
  * **A** | **gradient** :: [Type => Str | Array]		$Arg = gradfile+f1|2|3|4|5 | (data=Array, format=x)$

    The solution will partly be constrained by surface gradients v = v*n, where v is the   gradient magnitude and n its unit vector direction.
  * **C** | **approx** | **approximate** :: [Type => Str | Number]	$Arg = [n]value[+ffile]$

    Find an approximate surface fit: Solve the linear system for the spline coefficients by   SVD and eliminate the contribution from all eigenvalues whose ratio to the largest   eigenvalue is less than value.
  * **G** | **grid** :: [Type => Str | []]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = greenspline(....) form.
  * **D** | **metadata** | **mode** :: [Type => Number]

    Sets the distance flag that determines how we calculate distances between data points.
  * **E** :|**misfit** :: [Type => Str | []]		$Arg = [misfitfile]$

    Evaluate the spline exactly at the input data locations and report statistics of   the misfit (mean, standard deviation, and rms).
  * **L** | **leave_trend** :: [Type => Bool]

    Do not remove a linear (1-D) or planer (2-D) trend when -D selects mode 0-3.
  * **N** | **nodes** :: [Type => Number | Array]			$Arg = nodefile$

    ASCII file with coordinates of desired output locations x in the first column(s).
  * **Q** | **dir_derivative** :: [Type => Str]		$Arg = az|x/y/z$

    Rather than evaluate the surface, take the directional derivative in the az azimuth and   return the magnitude of this derivative instead.
  * **S** | **splines** :: [Type => Str]				$Arg = c|t|l|r|p|q[pars]$

    Select one of six different splines. The first two are used for 1-D, 2-D, or 3-D Cartesian splines.
  * **T** | **mask** :: [Type => Str]					$Arg = maskgrid$

    For 2-D interpolation only. Only evaluate the solution at the nodes in the maskgrid that are   not equal to NaN.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **uncertainties** :: [Type => Str | []]	$Arg = [w]$

```
Data one-sigma uncertainties are provided in the last column. We then compute weights that
are inversely proportional to the uncertainties squared.
```

  * **Z** | **mode** | **distmode** :: [Type => Str | number]

    Sets the distance mode that determines how we calculate distances between data points.
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    Force pixel node registration [Default is gridline registration].
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    Limit the number of cores to be used in any OpenMP-enabled multi-threaded algorithms.   (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? greenspline$
