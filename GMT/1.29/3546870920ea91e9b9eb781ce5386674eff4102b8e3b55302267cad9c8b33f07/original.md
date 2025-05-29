```
grdtrend(cmd0::String="", arg1=nothing, arg2=nothing; kwargs...)
```

reads a 2-D grid file and fits a low-order polynomial trend to these data by [optionally weighted] least-squares.

## Parameters

  * **N** | **model** :: [Type => Str | Number]

    Sets the number of model parameters to fit.
  * **D** | **diff** :: [Type => Str | []]

    Compute the difference (input data - trend). Optionaly provide a file name to save result on disk.
  * **T** | **trend** :: [Type => Str | []]

    Compute the trend surface. Optionaly provide a file name to save result on disk.
  * **W** | **weights** :: [Type => Str]

    If weight.nc exists, it will be read and used to solve a weighted least-squares problem.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.

To see the full documentation type: $@? grdtrend$
