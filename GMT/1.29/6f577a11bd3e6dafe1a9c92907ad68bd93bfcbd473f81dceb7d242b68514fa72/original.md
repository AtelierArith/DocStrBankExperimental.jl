```
mblevitus(cmd0::String=""; kwargs...)
```

Create a water velocity profile which is representative of the mean annual water column for a specified 1 degree by 1 degree region.

## Parameters

  * **A** | **all4** :: [Type => Bool]

    Pint also depth, velocity, temperature, salinity.
  * **L** | **location** :: [Type => Str | Tuple]		$Arg = lon/lat$

    Sets the longitude and latitude of the location of the water velocity profile.
  * **O** | **outfile** | **out_file** :: [Type => Str]

    Write the SVP to <outfile>.
  * **H** | **help** :: [Type => Bool]

    Print out program's description.
  * **z** | **z_down** :: [Type => Bool]

    Makes Z axes positive down (default here is Z-up).
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
