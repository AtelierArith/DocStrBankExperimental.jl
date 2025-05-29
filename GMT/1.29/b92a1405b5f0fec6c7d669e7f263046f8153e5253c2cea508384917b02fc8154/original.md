```
gravmag3d(cmd0::String=""; kwargs...)
```

Compute the gravity/magnetic anomaly of a 3-D body by the method of Okabe.

See full GMT (not the `GMT.jl` one) docs at [`gmtgravmag3d`](http://docs.generic-mapping-tools.org/latest/supplements/potential/gmtgravmag3d.html)

## Parameters

  * **C** | **density** :: [Type => Str | GMTgrid]

    Sets body density in SI. Provide either a constant density or a grid with a variable one.
  * **F** | **track** :: [Type => Str | Matrix | GMTdataset]

    Provide locations where the anomaly will be computed. Note this option is mutually exclusive with `outgrid`.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = gmtgravmag3d(....) form.
  * **H** | **mag_params** :: [Type => Number]

    Sets parameters for computation of magnetic anomaly. Alternatively, provide a magnetic intensity grid.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **L** | **z_obs** | **observation_level** :: [Type => Number]

    Sets level of observation [Default = 0]. That is the height (z) at which anomalies are computed.
  * **M** | **body** :: [Type => Str | Tuple]

    Create geometric bodies and compute their grav/mag effect.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **radius** :: [Type => Number]

    Set search radius in km (valid only in the two grids mode OR when `thickness`) [Default = 30 km].
  * **T+v** | **index** :: [Type => Str]
  * **T+r** | **raw_triang** :: [Type => Str]
  * **T+s** | **stl** :: [Type => Str]

    Gives names of a xyz and vertex (ndex="vert_file") files defining a close surface.
  * **Z** | **level** | **reference_level** :: [Type => Number]

    Level of reference plane [Default = 0].

### Example

```julia
	G = gmtgravmag3d(M=(shape=:prism, params=(1,1,1,5)), inc=1.0, region="-15/15/-15/15", mag_params="10/60/10/-10/40");
	imshow(G)
```
