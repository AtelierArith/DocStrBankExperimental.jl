```
grdclip(cmd0::String="", arg1=nothing; kwargs...)
```

Clip the range of grid values. will set values < low to below and/or values > high to above. You can also specify one or more intervals where all values should be set to $between$, or replace individual values.

See full GMT (not the `GMT.jl` one) docs at [`grdclip`](http://docs.generic-mapping-tools.org/latest/grdclip.html)

## Parameters

  * **cmd0** :: [Type => Str]

    The input file name. Do not use this when the grid (a GMTgrid type) is passed via the $arg1$ argument.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdclip(....) form.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **above** | **high** :: [Type => Array | Str]

    Two elements array with $high$ and $above$ or a string with "high/above".   It sets all data[i] > $high$ to $above$.
  * **below** | **low** :: [Type => Array | Str]

    Two elements array with $low$ and $below$ or a string with "low/below".   It sets all data[i] < $low$ to $below$.
  * **between** :: [Type => Array | Str]

    Three elements array with $low, high$ and $between$ or a string with "low/high/between".   It sets all data[i] >= $low$ and <= $high$ to $between$.
  * **old** | **new** :: [Type => Array | Str]

    Two elements array with $old$ and $new$ or a string with "old/new".   It sets all data[i] == $old$ to $new$.
  * **S** :: [Type => Str]

    Condense all replacement options above in a single string.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * Examples:

    ```
      G=gmt("grdmath", "-R0/10/0/10 -I1 X");
      G2=grdclip(G, above=[5 6], low=[2 2], between="3/4/3.5")
    ```

    or (note the use of -S for second on options because we can't repeat a kwarg name)

    ```
      G2=grdclip(G, S="a5/6 -Sb2/2 -Si3/4/3.5")
    ```
