```
gmtinfo(cmd0::String="", arg1=nothing; kwargs...)
```

Reads files and finds the extreme values in each of the columns.

## Parameters

  * **A** | **ranges** :: [Type => Str]

    Specify how the range should be reported.
  * **C** | **numeric** | **per_column** :: [Type => Bool]

    Report the min/max values per column in separate columns [Default uses <min/max> format].
  * **D** | **center** :: [Type => Bool]

    Modifies results obtained by -I by shifting the region to better align with the center of the data.
  * **E** | **get_record** :: [Type => Str | []]

    Returns the record whose column col contains the minimum (l) or maximum (h) value.
  * **F** | **counts** :: [Type => Str | []]

    Returns the counts of various records depending on the appended mode.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str | Number | Tuple]

    Report the min/max of the first n columns to the nearest multiple of the provided increments   and output results in the form -Rw/e/s/n
  * **L** | **common_limits** :: [Type => Bool]

    Determines common limits across tables or segments.
  * **S** | **for*error*bars** :: [Type => Str | []]

    Add extra space for error bars. Useful together with I option and when later plotting with `plot E`.
  * **T** | **nearest_multiple** :: [Type => Str | Number]    $Arg = dz[+ccol]$

    Report the min/max of the first (0’th) column to the nearest multiple of dz and output this as   the string -Tzmin/zmax/dz.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    Save result to ASCII file instead of returning to a Julia variable. Give file name as argument.   Use the bo option to save as a binary file.
  * **append** :: [Type => Str]     $Arg = fname$

    Append result to an existing file named $fname$ instead of returning to a Julia variable.   Use the bo option to save as a binary file.

To see the full documentation type: $@? grdmask$
