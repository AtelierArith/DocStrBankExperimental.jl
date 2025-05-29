```
mbsvplist(cmd0::String=""; kwargs...)
```

List water sound velocity profiles in swath sonar data files.

## Parameters

  * **C** | **uniquesvp** :: [Type => Bool]

    Output the number of unique SVPs in each file.
  * **F** | **format** :: [Type => Int]

    Sets the format for the input swath sonar data.
  * **M** | **mode** :: [Type => Int]		$Arg = 1 or 2 or 3$

    Sets the SVP output mode..
  * **S** | **ssv** :: [Type => Bool]

    Sets the minimum speed in km/hr (5.5 kts ~ 10 km/hr) allowed in the input data.
  * **Z** | **firstiszero** :: [Type => Bool]

    Sets the style of the plot.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
