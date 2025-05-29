```
grdpaste(cmd0::String="", G1=nothing, G2=nothing, kwargs...)
```

Combine grids $grid1$ and $grid2$ into $grid3$ by pasting them together along their common edge. Both grids must have the same dx, dy and have one edge in common.

See full GMT (not the `GMT.jl` one) docs at [`grdpaste`](http://docs.generic-mapping-tools.org/latest/grdpaste.html)

## Parameters

  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdpaste(....) form.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

To see the full documentation type: $@? grdpaste$
