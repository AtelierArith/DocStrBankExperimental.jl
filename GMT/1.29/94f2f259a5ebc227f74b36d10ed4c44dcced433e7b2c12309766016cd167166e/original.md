```
grdgravmag3d(cmd0::String="", arg1=nothing, arg2=nothing; kwargs...)
```

Compute the gravity/magnetic anomaly of the volume contained between a surface provided by one grid and a plane, or between a top and a bottom surface provided by two grids.

See full GMT (not the `GMT.jl` one) docs at [`grdgravmag3d`](http://docs.generic-mapping-tools.org/latest/supplements/potential/grdgravmag3d.html)

## Parameters

  * **C** | **density** :: [Type => Str | GMTgrid]

    Sets body density in SI. Provide either a constant density or a grid with a variable one.
  * **F** | **track** :: [Type => Str | Matrix | GMTdataset]

    Provide locations where the anomaly will be computed. Note this option is mutually exclusive with `outgrid`.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = grdgravmag3d(....) form.
  * **E** | **thickness** :: [Type => Number]

    Provide the layer thickness in m [Default = 500 m].
  * **H** | **mag_params** :: [Type => Number]

    Sets parameters for computation of magnetic anomaly. Alternatively, provide a magnetic intensity grid.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **L** | **z_obs** | **observation_level** :: [Type => Number]

    Sets level of observation [Default = 0]. That is the height (z) at which anomalies are computed.
  * **Q** | **pad** :: [Type => Number]

    Extend the domain of computation with respect to output `region`.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **radius** :: [Type => Number]

    Set search radius in km (valid only in the two grids mode OR when `thickness`) [Default = 30 km].
  * **Z** | **level** | **reference_level** :: [Type => Number]

    Level of reference plane [Default = 0].
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    Limit the number of cores to be used in any OpenMP-enabled multi-threaded algorithms.   (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)

### Example. Compute the gravity effect of the Gorringe bank.

```julia
	G = grdgravmag3d("@earth_relief_10m", region=(-12.5,-10,35.5,37.5), density=2700, inc=0.05, pad=0.5, z_level=:bottom, f=:g);
	imshow(G)
```
