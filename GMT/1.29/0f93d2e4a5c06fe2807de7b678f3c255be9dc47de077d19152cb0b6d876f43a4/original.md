```
mapproject(cmd0::String="", arg1=nothing, kwargs...)
```

Forward and inverse map transformations, datum conversions and geodesy.

See full GMT (not the `GMT.jl` one) docs at [`mapproject`](http://docs.generic-mapping-tools.org/latest/mapproject.html)

## Parameters

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    Specify the region of interest. Set to data minimum BoundinBox if not provided.
  * **J** | **proj** | **projection** :: [Type => String]

    Select map projection. Defaults to 15x10 cm with linear (non-projected) maps.
  * **A** | **azim**  | **azimuth**:: [Type => Str]    $Arg = b|B|f|F|o|O[lon0/lat0][+v]$

    Calculate azimuth along track or to the optional fixed point set with lon0/lat0.
  * **C** | **center** :: [Type => Str | List | []]     $Arg = [dx/dy]$

    Set center of projected coordinates to be at map projection center [Default is lower left corner].
  * **D** | **lengthunit** :: [Type => Str]    $Arg = c|i|p$

    Temporarily override PROJ*LENGTH*UNIT and use c (cm), i (inch), or p (points) instead.
  * **E** | **geod2ecef** | **ecef** :: [Type => Str | []]    $Arg = [datum]$

    Convert from geodetic (lon, lat, height) to Earth Centered Earth Fixed (ECEF) (x,y,z) coordinates.
  * **F** | **one2one** :: [Type => Str | []]    $Arg = [unit]$

    Force 1:1 scaling, i.e., output (or input, see I) data are in actual projected meters.
  * **G** | **track_distances** :: [Type => Str | List]    $Arg = [lon0/lat0][+a][+i][+u[+|-]unit][+v]$

    Calculate distances along track or to the optional fixed point set with G="lon0/lat0".
  * **I** | **inverse** :: [Type => Bool]

    Do the Inverse transformation, i.e., get (longitude,latitude) from (x,y) data.
  * **L** | **dist2line** :: [Type => Str | NamedTuple]   $Arg = line.xy[+u[+|-]unit][+p] | (line=Matrix, unit=x, fractional_pt=_,cartesian=true, projected=true)$

    Determine the shortest distance from the input data points to the line(s) given in the   ASCII multisegment file line.xy.
  * **N** | **geod2aux** :: [Type => Str | []]       $Arg = [a|c|g|m]$

    Convert from geodetic latitudes to one of four different auxiliary latitudes (longitudes are unaffected).
  * **Q** | **list** :: [Type => Str | []]           $Arg = [d|e]$

    List all projection parameters. To only list datums, use Q=:d, to only list ellipsoids, use Q=:e.
  * **S** | **supress** :: [Type => Bool]

    Suppress points that fall outside the region.
  * **T** | **change_datum** :: [Type => Str]    $Arg = [h]from[/to]$

    Coordinate conversions between datums from and to using the standard Molodensky transformation.
  * **W** | **map_size** | **mapsize** :: [Type => Str | []]    $Arg = [w|h]$

    Prints map width and height on standard output. No input files are read.
  * **Z** | **traveltime** | **travel_times** :: [Type => Str | Number]    $Arg = [speed][+a][+i][+f][+tepoch]$

    Calculate travel times along track as specified with -G.
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    Control how user-coded missing data values are translated to official NaN values in GMT.
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    Only accept ASCII data records that contains the specified pattern.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    Examine the spacing between consecutive data points in order to impose breaks in the line.
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    Primary input file(s) has header record(s).
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    Select specific data columns for primary input, in arbitrary order.
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    Select specific data columns for primary output, in arbitrary order.
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    Selects perspective view and sets the azimuth and elevation of the viewpoint [180/90].
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    Suppress output for records whose z-value equals NaN.
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    Swap 1st and 2nd column on input and/or output.

To see the full documentation type: $@? mapproject$
