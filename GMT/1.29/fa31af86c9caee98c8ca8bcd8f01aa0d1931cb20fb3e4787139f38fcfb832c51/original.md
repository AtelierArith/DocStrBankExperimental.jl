```
blockmean(cmd0::String="", arg1=nothing; kwargs...)
```

Block average (x,y,z) data tables by L2 norm.

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **A** | **field** | **fields** :: [Type => Str]

    Select which fields to write to individual grids. Append comma-separated codes for available   fields: **z** (the mean data z, but see **statistic**), **s** (standard deviation), **l** (lowest value),   **h** (highest value) and **w** (the output weight; requires **weights**). [Default is just **z**].
  * **C** | **center** :: [Type => Bool]

    Use the center of the block as the output location [Default uses the mean location]. Not used when **-A**
  * **E** | **extend** | **extended** :: [Type => Str | []]

    Provide Extended report which includes s (the standard deviation about the mean), l, the lowest   value, and h, the high value for each block. Output order becomes x,y,z,s,l,h[,w]. [Default   outputs x,y,z[,w]. See -W for w output. If -Ep is used we assume weights are 1/(sigma squared)   and s becomes the propagated error of the mean.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Write one or more fields directly to grids on disk; no table data are return. If more than one   fields are specified via **A** then grdfile must contain the format flag %s so that we can embed the   field code in the file names. If not provided but **A** is used, return 1 or more GMTgrid type(s).
  * **S** | **statistic** :: [Type => Str | Symb] 

    Use `statistic=:n` to report the number of points inside each block, `statistic=:s` to report the sum of all z-values    inside a block, `statistic=:w` to report the sum of weights [Default (or `statistic=:m` reports mean value].
  * **mean** :: [Type => Any] 

    Report the mean value of points inside each block
  * **npts** | **counts** :: [Type => Any] 

    Report the number of points inside each block
  * **sum** :: [Type => Any] 

    Report the sum of all z-values inside each block
  * **sum_weights** :: [Type => Any] 

    Report the the sum of weights
  * **grid** :: [Type => Bool] 

    With any of the above options (`statistic`, `npts`, `sum`) this option makes it return a grid instead of a GMTdataset.
  * **W** | **weights** :: [Type => Str | []]

    Unweighted input and output have 3 columns x,y,z; Weighted i/o has 4 columns x,y,z,w. Weights can   be used in input to construct weighted mean values for each block.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? blockmean$
