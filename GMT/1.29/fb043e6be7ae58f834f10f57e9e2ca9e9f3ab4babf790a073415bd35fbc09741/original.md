```
trend2d(cmd0::String="", arg1=nothing, kwargs...)
```

Fit a [weighted] [robust] polynomial model for z = f(x,y) to xyz[w] data.

See full GMT (not the `GMT.jl` one) docs at [`trend2d`](http://docs.generic-mapping-tools.org/latest/trend2d.html)

## Parameters

  * **F** | **out** | **output** :: [Type => Str]   $Arg = xyzmrw|p$

    Specify up to five letters from the set {x y m r w} in any order to create columns of output.
  * **N** | **model** :: [Type => Str]      $Arg = n_model[+r]$

    Specify the number of terms in the model, n_model, and append +r to do a robust fit. E.g.,   a robust bilinear model is N="4+r".
  * **C** | **condition_number** :: [Type => Number]   $Arg = condition_number$

    Set the maximum allowed condition number for the matrix solution.
  * **I** | **conf_level** :: [Type => Number | []]   $Arg = [confidence_level]$

    Iteratively increase the number of model parameters, starting at one, until n*model is reachedx   or the reduction in variance of the model is not significant at the confidence*level level.
  * **W** | **weights** :: [Type => Str | []]     $Arg = [+s]$

    Weights are supplied in input column 4. Do a weighted least squares fit [or start with   these weights when doing the iterative robust fit].
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
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
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    Convert input records to a cyclical coordinate.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? trend2d$
