```
filter1d(cmd0::String="", arg1=nothing, kwargs...)
```

Time domain filtering of 1-D data tables.

## Parameters

  * **F** | **filter** :: [Type => Str]   `Arg = type width[modifiers]`

    Sets the filter type. Choose among convolution and non-convolution filters. Append the   filter code followed by the full filter width in same units as time column.
  * **D** | **inc** | **increment** :: [Type => Number]        `Arg = increment`

    $increment$ is used when series is NOT equidistantly sampled. Then increment will be the abscissae resolution.
  * **E** | **end** | **ends** :: [Type => Bool | []]

    Include Ends of time series in output. Default loses half the filter-width of data at each end.
  * **L** | **gap_width** :: [Type => Number | Str]      `Arg = width`

    Checks for Lack of data condition. If input data has a gap exceeding width then no output will be given at that point.
  * **N** | **time_col** | **timecol** :: [Type => Int]      `Arg = t_col`

    Indicates which column contains the independent variable (time). The left-most column   is # 0, the right-most is # (n_cols - 1). [Default is 0].
  * **Q** | **quality** :: [Type => Number]    `Arg = q_factor`

    Assess Quality of output value by checking mean weight in convolution. Enter q_factor between 0 and 1.
  * **S** | **symmetry** :: [Type => Number]    `Arg = symmetry_factor`

    Checks symmetry of data about window center. Enter a factor between 0 and 1.
  * **T** | **range** | **inc** :: [Type => List | Str]     `Arg = [min/max/]inc[+a|n]`

    Make evenly spaced time-steps from min to max by inc [Default uses input times].
  * `cumdist` | `cumsum`: [Type => Bool]

    Compute the cumulative distance along the input line. Note that for this the first two columns   must contain the spatial coordinates.

To see the full documentation type: $@? filter1d$
