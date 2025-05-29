```
sample1d(cmd0::String="", arg1=nothing, kwargs...)
```

Resample 1-D table data using splines

## Parameters

  * **A** | **resample** :: [Type => Str]        $Arg = f|p|m|r|R$

    For track resampling (if -T…unit is set) we can select how this is to be performed.
  * **E** | **keeptext** :: [Type => Bool]

    If the input dataset contains records with trailing text then we will attempt to add these to   output records that exactly match the input times.
  * **F** | **interp** :: [Type => Str]   $Arg = l|a|c|n|s<p>[+1|+2]$

    Choose from l (Linear), a (Akima spline), c (natural cubic spline), and n (no interpolation:   nearest point) [Default is Akima].
  * **N** | **time_col** :: [Type => Int]      $Arg = t_col$

    Indicates which column contains the independent variable (time). The left-most column   is # 0, the right-most is # (n_cols - 1). [Default is 0].
  * **T** | **inc** | **range** :: [Type => List | Str]     $Arg = [min/max/]inc[+a|n]] or file|list$

    Evaluate the best-fit regression model at the equidistant points implied by the arguments.
  * `cumdist` | `cumsum`: [Type => Bool]

    Compute the cumulative distance along the input line. Note that for this the first two columns   must contain the spatial coordinates.
  * `fill_nans` | `interp_nans`: [Type => Bool]

    Replace all NaN fields with the interpolated values from their neighbors.
  * `nonans`: [Type => Bool]

    Remove all rows that have NaN fields.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **W** | **weights** :: [Type => Int]     $Arg = w_col$

    Sets the column number of the weights to be used with a smoothing cubic spline. Requires Fs.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.
  * **append** :: [Type => Str]     $Arg = fname$

    Append result to an existing file named $fname$ instead of returning to a Julia variable.   Use the bo option to save as a binary file.
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    Examine the spacing between consecutive data points in order to impose breaks in the line.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? sample1d$
