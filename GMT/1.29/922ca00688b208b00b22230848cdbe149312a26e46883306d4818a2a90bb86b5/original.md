```
grdhisteq(cmd0::String="", arg1=nothing, kwargs...)
```

Find the data values which divide a given grid file into patches of equal area. One common use of grdhisteq is in a kind of histogram equalization of an image.

See full GMT (not the `GMT.jl` one) docs at [`grdhisteq`](http://docs.generic-mapping-tools.org/latest/grdhisteq.html)

## Parameters

  * **C** | **ncels** | **n_cels** :: [Type => Number]

    Sets how many cells (or divisions) of data range to make [16].
  * **D** | **dump** :: [Type => Str or []]

    Dump level information to file, or standard output if no file is provided.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdhisteq(....) form.
  * **N** | **gaussian** :: [Type => Number or []]

    Gaussian output.
  * **Q** | **quadratic** :: [Type => Bool]

    Quadratic output. Selects quadratic histogram equalization. [Default is linear].
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.

To see the full documentation type: $@? grdhisteq$
