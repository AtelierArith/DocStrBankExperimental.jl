```
kml2gmt(cmd0::String="", arg1=nothing, kwargs...)
```

kml2gmt - Extract GMT table data from Google Earth KML files

See full GMT (not the `GMT.jl` one) docs at [`kml2gmt`](http://docs.generic-mapping-tools.org/latest/kml2gmt.html)

## Parameters

  * **F** | **feature_type** :: [Type => Str]        $Arg = s|l|p$

    Specify a particular feature type to output. Choose from points (s), line (l), or polygon (p).   By default we output all geometries.
  * **Z** | **altitudes** :: [Type => Bool]

    Output the altitude coordinates as GMT z coordinates [Default will output just longitude and latitude].   (http://docs.generic-mapping-tools.org/latest/kml2gmt.html#z)
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    Select native binary output.
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    Examine all output columns and if any item equals NAN substitute it with   the chosen missing data value.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? kml2gmt$
