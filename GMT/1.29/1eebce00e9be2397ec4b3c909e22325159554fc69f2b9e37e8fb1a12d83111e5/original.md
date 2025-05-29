```
gravprisms(cmd0::String="", arg1=nothing; kwargs...)
```

Compute the gravity/magnetic anomaly of a 3-D body by the method of Okabe.

See full GMT (not the `GMT.jl` one) docs at [`gravprisms`](http://docs.generic-mapping-tools.org/latest/supplements/potential/gravprisms.html)

## Parameters

  * **A** | **zup** :: [Type => Bool]

    The z-axis should be positive upwards [Default is down].
  * **D** | **density** :: [Type => Str | GMTgrid]

    Sets body density in SI. Provide either a constant density or a grid with a variable one.
  * **E** | **dxdy** | **xy_sides** :: [Type => Number | Tuple numbers]

    If all prisms in table have constant x/y-dimensions then they can be set here. In that case table must~   only contain the centers of each prism and the z range
  * **F** | **component** :: [Type => Str]

    Specify desired gravitational field component.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name. Note that this is optional and to be used only when saving   the result directly on disk. Otherwise, just use the G = gravprisms(....) form.
  * **H** | **radial_rho** :: [Type => Str | Tuple]

    Set reference seamount parameters for an ad-hoc variable radial density function with depth.
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [and optionally *y_inc*] is the grid spacing. Optionally, append an increment unit.
  * **L** | **base** :: [Type => Number ! Grid]

    Give name of the base surface grid for a layer we wish to approximate with prisms, or give a constant z-level [0].
  * **M** | **units** :: [Type => Str]

    Sets distance units used. units=:horizontal to indicate that both horizontal distances are in km [m].
  * **N** | **track** :: [Type => Str | Matrix | GMTdataset]

    Specifies individual (x, y[, z]) locations where we wish to compute the predicted value.
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **S** | **topography** :: [Type => Number]

    Give name of grid with the full seamount heights, either for making prisms or as required by H.
  * **T** | **top** :: [Type => Number | Grid]

    Give name of the top surface grid for a layer we wish to approximate with prisms, or give a constant z-level.
  * **Z** | **z_obs** | **observation_level** :: [Type => Number | Grid]

    Set observation level, either as a constant or variable by giving the name of a grid with observation levels.
  * **T** | **top** :: [Type => Number | Grid]

    Give name of the top surface grid for a layer we wish to approximate with prisms, or give a constant z-level.
  * **W** | **out*mean*rho** :: [Type => Str]

    Give name of an output grid with spatially varying, vertically-averaged prism densities created by C and H.
