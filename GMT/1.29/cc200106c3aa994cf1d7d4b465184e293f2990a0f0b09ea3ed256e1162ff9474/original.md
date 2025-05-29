```
regress(cmd0::String="", arg1=nothing, kwargs...)
```

Linear regression of 1-D data sets.

See full GMT (not the `GMT.jl` one) docs at [`regress`](http://docs.generic-mapping-tools.org/latest/gmtregress.html)

## Parameters

  * **A** | **all_slopes** :: [Type => Str | List]        $Arg = min/max/inc$

    Instead of determining a best-fit regression we explore the full range of regressions.
  * **C** | **ci** | **cl** | **confidence_level** :: [Type => Int]      $Arg = level$

    Set the confidence level (in %) to use for the optional calculation of confidence   bands on the regression [95].
  * **E** | **regression_type** :: [Type => Str]   $Arg = x|y|o|r$

    Type of linear regression, i.e., select the type of misfit we should calculate.
  * **F** | **column_combination** :: [Type => Str]   $Arg = x|y|m|l|c$

    Append a combination of the columns you wish returned;
  * **N** | **norm** :: [Type => Str | Int]          $Arg = 1|2|r|w$

    Selects the norm to use for the misfit calculation.
  * **S** | **restrict** :: [Type => Str | []]        $Arg = [r]$

    Restricts which records will be output.
  * **T** | **equi_space** :: [Type => Str | List]     $Arg = [min/max/]inc[+a|n]] or file|list$

    Evaluate the best-fit regression model at the equidistant points implied by the arguments.
  * **W** | **weighted** :: [Type => Str | []]     $Arg = [w][x][y][r]$

    Specifies weighted regression and which weights will be provided.
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
