```
gmtisf(cmd0::String; kwargs...)
```

Read seismicity data in the a ISF formated file.

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **D** | **date** :: date="datestart[/dateend]"

    Limit the output to data >= datestart, or between datestart and dateend. <date> must be in ISO format, e.g, 2000-04-25.
  * **F** | **focal** :: [Type => Bool or Str or Symbol]

    Select only events that have focal mechanisms. The default is Global CMT convention. Use `focal=:a` for the AKI convention
  * **N** | **notime** :: [Type => Bool]

    Do NOT output time information.
  * `abstime or unixtime` :: [Type => Integer]

    Convert the YYYY, MM, DD, HH, MM columns into a unixtime. Default puts it as first column,   use `abstime=2` to put it as last column.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

This module can also be called via `gmtread`. *I.,e.* `gmtread("file.isf", opts...)_
