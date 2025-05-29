```
histogram(cmd0::String="", arg1=nothing; kwargs...)
```

Examines the first data column to calculate histogram parameters based on the bin-width provided. Alternatively, show histograms of GMTimage & GMTgrid objects directly. The options 'auto=true' or 'thresholds=(0, 0.1)' will find the histogram bounds convenient for contrast enhancement (histogram stretch). The values represent the percentage of countings used to estimate the boundings. The option 'zoom=true' will set 'auto=true' and show histogram only on the region of interest.

## Parameters

  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **A** | **horizontal** :: [Type => Bool]

    Plot the histogram horizontally from x = 0 [Default is vertically from y = 0].
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    Set map boundary frame and axes attributes.
  * **C** | **color** | **cmap** :: [Type => Str | GMTcpt]

    Give a CPT. The mid x-value for each bar is used to look-up the bar color.
  * **D** | **annot** | **annotate** | **counts** :: [Type => Str | Tuple]

    Annotate each bar with the count it represents.
  * **E** | **width** :: [Type => Bool]			`Arg = width[+ooffset]`

    Use an alternative histogram bar width than the default set via T, and optionally shift all bars by an offset.
  * **binmethod** | *BinMethod** :: [Type => Str]			`Arg = method`

    Binning algorithm: "scott", "fd", "sturges" or "sqrt" for floating point data. "second", "minute", "hour",   "day", "week", "month" or "year" for DateTime data.
  * **F** | **center** :: [Type => Bool]

    Center bin on each value. [Default is left edge].
  * **G** | **fill** :: [Type => Number | Str]

    Select filling of bars [if no G, L or C set G=100].
  * **I** | **inquire** | **bins** :: [Type => Bool | :O | :o | bins=(all=true,) | bins=(no_zero=true,) ]

    Inquire about min/max x and y after binning OR output the binned array.
  * **L** | **out_range** :: [Type => Str]			`Arg = l|h|b`

    Handling of extreme values that fall outside the range set by **T**.
  * **N** | **distribution** | **normal** :: [Type => Str]

    Draw the equivalent normal distribution; append desired pen [0.5p,black].
  * **P** | **portrait** :: [Type => Bool or []]

    Tell GMT to **NOT** draw in portrait mode (that is, make a Landscape plot)
  * **Q** | **cumulative** :: [Type => Bool | "r"]

    Draw a cumulative histogram. Append r to instead compute the reverse cumulative histogram.
  * **R** | **region** :: [Type => Str]

    Specifies the ‘region’ of interest in (r,azimuth) space. r0 is 0, r1 is max length in units.
  * **S** | **stairs** :: [Type => Str | number]

    Draws a stairs-step diagram which does not include the internal bars of the default histogram.
  * **T** | **range** | **bin** :: [Type => Str]			`Arg = [min/max/]inc[+n] | file|list]`

    Make evenly spaced array of bin boundaries from min to max by inc. If min/max are not given then we   default to the range in `region`. For constant bin width use `bin=val`..
  * **W** | **pen** :: [Type => Str | Tuple]

    Set pen attributes for sector outline or rose plot. [Default is no outline].
  * **Z** | **kind** :: [Type => Number | Str]

    Choose between 6 types of histograms.
  * **savefig** | **figname** | **name** :: [Type => Str]

    Save the figure with the `figname=name.ext` where `ext` chooses the figure format (e.g. figname="name.png")

To see the full documentation type: $@? histogram$
