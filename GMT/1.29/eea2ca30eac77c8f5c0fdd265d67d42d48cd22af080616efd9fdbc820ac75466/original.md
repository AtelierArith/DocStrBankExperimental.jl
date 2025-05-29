```
grdgradient(cmd0::String="", arg1=nothing, kwargs...)
```

Compute the directional derivative in a given direction, or to find the direction [and the magnitude] of the vector gradient of the data.

See full GMT (not the `GMT.jl` one) docs at [`grdgradient`](http://docs.generic-mapping-tools.org/latest/grdgradient.html)

## Parameters

  * **A** | **azim** | **azimuth** :: [Type => Str | Number]    $Arg = azim[/azim2]$

    Azimuthal direction for a directional derivative.
  * **D** | **find_dir** :: [Type => Str]      $Arg = [a][c][o][n]$

    Find the direction of the positive (up-slope) gradient of the data.
  * **G** | **save** | **write** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdgradient(....) form.
  * **E** | **lambert** :: [Type => Str]    $Arg = [m|s|p]azim/elev[+aambient][+ddiffuse][+pspecular][+sshine]$

    Compute Lambertian radiance appropriate to use with grdimage and grdview.
  * **N** | **norm** | **normalize** :: [Type => Str]     $Arg = [e|t][amp][+ssigma][+ooffset]$

    Normalization. [Default is no normalization.] The actual gradients g are offset and scaled   to produce normalized gradients.
  * **Q** | **save_stats** :: [Type => Str]		$Arg = c|r|R$

    Controls how normalization via N is carried out.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **slopegrid** :: [Type => Str]

    Name of output grid file with scalar magnitudes of gradient vectors. Requires D but makes G optional.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

To see the full documentation type: $@? grdgradient$
