```
gmtspectrum1d(cmd0::String="", arg1=nothing, kwargs...)
```

Compute auto- [and cross- ] spectra from one [or two] time-series.

See full GMT (not the `GMT.jl` one) docs at [`spectrum1d`](http://docs.generic-mapping-tools.org/latest/spectrum1d.html)

## Parameters

  * **S** | **size** :: [Type => Str]        $Arg = segment_size$

    $segment_size$ is a radix-2 number of samples per window for ensemble averaging.
  * **C** | **output** :: [Type => Str | []]        $Arg = [xycnpago]$

    Read the first two columns of input as samples of two time-series, X(t) and Y(t).   Consider Y(t) to be the output and X(t) the input in a linear system with noise.
  * **D** | **sample_dist** :: [Type => Number]   $Arg = dt$

    Set the spacing between samples in the time-series [Default = 1].
  * **L** | **leave_trend** :: [Type => Str | []]     $Arg = [h|m]$

Leave trend alone. By default, a linear trend will be removed prior to the transform.

  * **N** | **name** :: [Type => Int]      $Arg = t_col$

    Indicates which
  * **T** :: [Type => Bool]

    Disable the writing of a single composite results file to stdout.
  * **W** | **wavelength** :: [Type => Bool | Str]

    Write Wavelength rather than frequency in column 1 of the output file[s] [Default = frequency, (cycles / dt)].
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
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
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? spectrum1d$
